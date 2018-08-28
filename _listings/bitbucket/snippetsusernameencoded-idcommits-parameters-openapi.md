---
swagger: "2.0"
x-collection-name: Bitbucket
x-complete: 0
info:
  title: Bitbucket Parameters Snippets Username Encoded  Commits
  description: Parameters snippets username encoded  commits
  termsOfService: https://www.atlassian.com/legal/customer-agreement
  contact:
    name: Bitbucket Support
    url: https://support.atlassian.com/bitbucket
    email: support@bitbucket.org
  version: 1.0.0
host: api.bitbucket.org
basePath: /2.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /snippets:
    get:
      summary: Get Snippets
      description: |-
        Returns all snippets. Like pull requests, repositories and teams, the
        full set of snippets is defined by what the current user has access to.

        This includes all snippets owned by the current user, but also all snippets
        owned by any of the teams the user is a member of, or snippets by other
        users that the current user is either watching or has collaborated on (for
        instance by commenting on it).

        To limit the set of returned snippets, apply the
        `?role=[owner|contributor|member]` query parameter where the roles are
        defined as follows:

        * `owner`: all snippets owned by the current user
        * `contributor`: all snippets owned by, or watched by the current user
        * `member`: owned by the user, their teams, or watched by the current user

        When no role is specified, all public snippets are returned, as well as all
        privately owned snippets watched or commented on.

        The returned response is a normal paginated JSON list. This endpoint
        only supports `application/json` responses and no
        `multipart/form-data` or `multipart/related`. As a result, it is not
        possible to include the file contents.
      operationId: getSnippets
      x-api-path-slug: snippets-get
      parameters:
      - in: query
        name: role
        description: Filter down the result based on the authenticated users role
          (`owner`, `contributor`, or `member`)
      responses:
        200:
          description: OK
      tags:
      - Snippets
    parameters:
      summary: Parameters Snippets
      description: Parameters snippets
      operationId: parametersSnippets
      x-api-path-slug: snippets-parameters
      responses:
        200:
          description: OK
      tags:
      - Snippets
    post:
      summary: Add Snippets
      description: |-
        Creates a new snippet under the authenticated user's account.

        Snippets can contain multiple files. Both text and binary files are
        supported.

        The simplest way to create a new snippet from a local file:

            $ curl -u username:password -X POST https://api.bitbucket.org/2.0/snippets               -F file=@image.png

        Creating snippets through curl has a few limitations and so let's look
        at a more complicated scenario.

        Snippets are created with a multipart POST. Both `multipart/form-data`
        and `multipart/related` are supported. Both allow the creation of
        snippets with both meta data (title, etc), as well as multiple text
        and binary files.

        The main difference is that `multipart/related` can use rich encoding
        for the meta data (currently JSON).


        multipart/related (RFC-2387)
        ----------------------------

        This is the most advanced and efficient way to create a paste.

            POST /2.0/snippets/evzijst HTTP/1.1
            Content-Length: 1188
            Content-Type: multipart/related; start="snippet"; boundary="===============1438169132528273974=="
            MIME-Version: 1.0

            --===============1438169132528273974==
            Content-Type: application/json; charset="utf-8"
            MIME-Version: 1.0
            Content-ID: snippet

            {
              "title": "My snippet",
              "is_private": true,
              "scm": "hg",
              "files": {
                  "foo.txt": {},
                  "image.png": {}
                }
            }

            --===============1438169132528273974==
            Content-Type: text/plain; charset="us-ascii"
            MIME-Version: 1.0
            Content-Transfer-Encoding: 7bit
            Content-ID: "foo.txt"
            Content-Disposition: attachment; filename="foo.txt"

            foo

            --===============1438169132528273974==
            Content-Type: image/png
            MIME-Version: 1.0
            Content-Transfer-Encoding: base64
            Content-ID: "image.png"
            Content-Disposition: attachment; filename="image.png"

            iVBORw0KGgoAAAANSUhEUgAAABQAAAAoCAYAAAD+MdrbAAABD0lEQVR4Ae3VMUoDQRTG8ccUaW2m
            TKONFxArJYJamCvkCnZTaa+VnQdJSBFl2SMsLFrEWNjZBZs0JgiL/+KrhhVmJRbCLPx4O+/DT2TB
            cbblJxf+UWFVVRNsEGAtgvJxnLm2H+A5RQ93uIl+3632PZyl/skjfOn9Gvdwmlcw5aPUwimG+NT5
            EnNN036IaZePUuIcK533NVfal7/5yjWeot2z9ta1cAczHEf7I+3J0ws9Cgx0fsOFpmlfwKcWPuBQ
            73Oc4FHzBaZ8llq4q1mr5B2mOUCt815qYR8eB1hG2VJ7j35q4RofaH7IG+Xrf/PfJhfmwtfFYoIN
            AqxFUD6OMxcvkO+UfKfkOyXfKdsv/AYCHMLVkHAFWgAAAABJRU5ErkJggg==
            --===============1438169132528273974==--

        The request contains multiple parts and is structured as follows.

        The first part is the JSON document that describes the snippet's
        properties or meta data. It either has to be the first part, or the
        request's `Content-Type` header must contain the `start` parameter to
        point to it.

        The remaining parts are the files of which there can be zero or more.
        Each file part should contain the `Content-ID` MIME header through
        which the JSON meta data's `files` element addresses it. The value
        should be the name of the file.

        `Content-Disposition` is an optional MIME header. The header's
        optional `filename` parameter can be used to specify the file name
        that Bitbucket should use when writing the file to disk. When present,
        `filename` takes precedence over the value of `Content-ID`.

        When the JSON body omits the `files` element, the remaining parts are
        not ignored. Instead, each file is added to the new snippet as if its
        name was explicitly linked (the use of the `files` elements is
        mandatory for some operations like deleting or renaming files).


        multipart/form-data
        -------------------

        The use of JSON for the snippet's meta data is optional. Meta data can
        also be supplied as regular form fields in a more conventional
        `multipart/form-data` request:

            $ curl -X POST -u credentials https://api.bitbucket.org/2.0/snippets               -F title="My snippet"               -F file=@foo.txt -F file=@image.png

            POST /2.0/snippets HTTP/1.1
            Content-Length: 951
            Content-Type: multipart/form-data; boundary=----------------------------63a4b224c59f

            ------------------------------63a4b224c59f
            Content-Disposition: form-data; name="file"; filename="foo.txt"
            Content-Type: text/plain

            foo

            ------------------------------63a4b224c59f
            Content-Disposition: form-data; name="file"; filename="image.png"
            Content-Type: application/octet-stream

            ?PNG

            IHDR?1??I.....
            ------------------------------63a4b224c59f
            Content-Disposition: form-data; name="title"

            My snippet
            ------------------------------63a4b224c59f--

        Here the meta data properties are included as flat, top-level form
        fields. The file attachments use the `file` field name. To attach
        multiple files, simply repeat the field.

        The advantage of `multipart/form-data` over `multipart/related` is
        that it can be easier to build clients.

        Essentially all properties are optional, `title` and `files` included.


        Sharing and Visibility
        ----------------------

        Snippets can be either public (visible to anyone on Bitbucket, as well
        as anonymous users), or private (visible only to the owner, creator
        and members of the team in case the snippet is owned by a team). This
        is controlled through the snippet's `is_private` element:

        * **is_private=false** -- everyone, including anonymous users can view
          the snippet
        * **is_private=true** -- only the owner and team members (for team
          snippets) can view it

        To create the snippet under a team account, just append the team name
        to the URL (see `/2.0/snippets/{username}`).
      operationId: postSnippets
      x-api-path-slug: snippets-post
      parameters:
      - in: body
        name: _body
        description: The new snippet object
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Snippets
  /snippets/{username}:
    get:
      summary: Get Snippets Username
      description: |-
        Identical to `/snippets`, except that the result is further filtered
        by the snippet owner and only those that are owned by `{username}` are
        returned.
      operationId: getSnippetsUsername
      x-api-path-slug: snippetsusername-get
      parameters:
      - in: query
        name: role
        description: Filter down the result based on the authenticated users role
          (`owner`, `contributor`, or `member`)
      - in: path
        name: username
        description: Limits the result to snippets owned by this user
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
    parameters:
      summary: Parameters Snippets Username
      description: Parameters snippets username
      operationId: parametersSnippetsUsername
      x-api-path-slug: snippetsusername-parameters
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
    post:
      summary: Add Snippets Username
      description: |-
        Identical to `/snippets`, except that the new snippet will be
        created under the account specified in the path parameter `{username}`.
      operationId: postSnippetsUsername
      x-api-path-slug: snippetsusername-post
      parameters:
      - in: body
        name: _body
        description: The new snippet object
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
  /snippets/{username}/{encoded_id}:
    delete:
      summary: Delete Snippets Username Encoded
      description: Deletes a snippet and returns an empty response.
      operationId: deleteSnippetsUsernameEncoded
      x-api-path-slug: snippetsusernameencoded-id-delete
      parameters:
      - in: path
        name: encoded_id
        description: The snippets id
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
    get:
      summary: Get Snippets Username Encoded
      description: |-
        Retrieves a single snippet.

        Snippets support multiple content types:

        * application/json
        * multipart/related
        * multipart/form-data


        application/json
        ----------------

        The default content type of the response is `application/json`.
        Since JSON is always `utf-8`, it cannot reliably contain file contents
        for files that are not text. Therefore, JSON snippet documents only
        contain the filename and links to the file contents.

        This means that in order to retrieve all parts of a snippet, N+1
        requests need to be made (where N is the number of files in the
        snippet).


        multipart/related
        -----------------

        To retrieve an entire snippet in a single response, use the
        `Accept: multipart/related` HTTP request header.

            $ curl -H "Accept: multipart/related" https://api.bitbucket.org/2.0/snippets/evzijst/1

        Response:

            HTTP/1.1 200 OK
            Content-Length: 2214
            Content-Type: multipart/related; start="snippet"; boundary="===============1438169132528273974=="
            MIME-Version: 1.0

            --===============1438169132528273974==
            Content-Type: application/json; charset="utf-8"
            MIME-Version: 1.0
            Content-ID: snippet

            {
              "links": {
                "self": {
                  "href": "https://api.bitbucket.org/2.0/snippets/evzijst/kypj"
                },
                "html": {
                  "href": "https://bitbucket.org/snippets/evzijst/kypj"
                },
                "comments": {
                  "href": "https://api.bitbucket.org/2.0/snippets/evzijst/kypj/comments"
                },
                "watchers": {
                  "href": "https://api.bitbucket.org/2.0/snippets/evzijst/kypj/watchers"
                },
                "commits": {
                  "href": "https://api.bitbucket.org/2.0/snippets/evzijst/kypj/commits"
                }
              },
              "id": kypj,
              "title": "My snippet",
              "created_on": "2014-12-29T22:22:04.790331+00:00",
              "updated_on": "2014-12-29T22:22:04.790331+00:00",
              "is_private": false,
              "files": {
                "foo.txt": {
                  "links": {
                    "self": {
                      "href": "https://api.bitbucket.org/2.0/snippets/evzijst/kypj/files/367ab19/foo.txt"
                    },
                    "html": {
                      "href": "https://bitbucket.org/snippets/evzijst/kypj#file-foo.txt"
                    }
                  }
                },
                "image.png": {
                  "links": {
                    "self": {
                      "href": "https://api.bitbucket.org/2.0/snippets/evzijst/kypj/files/367ab19/image.png"
                    },
                    "html": {
                      "href": "https://bitbucket.org/snippets/evzijst/kypj#file-image.png"
                    }
                  }
                }
              ],
              "owner": {
                "username": "evzijst",
                "display_name": "Erik van Zijst",
                "uuid": "{d301aafa-d676-4ee0-88be-962be7417567}",
                "links": {
                  "self": {
                    "href": "https://api.bitbucket.org/2.0/users/evzijst"
                  },
                  "html": {
                    "href": "https://bitbucket.org/evzijst"
                  },
                  "avatar": {
                    "href": "https://bitbucket-staging-assetroot.s3.amazonaws.com/c/photos/2013/Jul/31/erik-avatar-725122544-0_avatar.png"
                  }
                }
              },
              "creator": {
                "username": "evzijst",
                "display_name": "Erik van Zijst",
                "uuid": "{d301aafa-d676-4ee0-88be-962be7417567}",
                "links": {
                  "self": {
                    "href": "https://api.bitbucket.org/2.0/users/evzijst"
                  },
                  "html": {
                    "href": "https://bitbucket.org/evzijst"
                  },
                  "avatar": {
                    "href": "https://bitbucket-staging-assetroot.s3.amazonaws.com/c/photos/2013/Jul/31/erik-avatar-725122544-0_avatar.png"
                  }
                }
              }
            }

            --===============1438169132528273974==
            Content-Type: text/plain; charset="us-ascii"
            MIME-Version: 1.0
            Content-Transfer-Encoding: 7bit
            Content-ID: "foo.txt"
            Content-Disposition: attachment; filename="foo.txt"

            foo

            --===============1438169132528273974==
            Content-Type: image/png
            MIME-Version: 1.0
            Content-Transfer-Encoding: base64
            Content-ID: "image.png"
            Content-Disposition: attachment; filename="image.png"

            iVBORw0KGgoAAAANSUhEUgAAABQAAAAoCAYAAAD+MdrbAAABD0lEQVR4Ae3VMUoDQRTG8ccUaW2m
            TKONFxArJYJamCvkCnZTaa+VnQdJSBFl2SMsLFrEWNjZBZs0JgiL/+KrhhVmJRbCLPx4O+/DT2TB
            cbblJxf+UWFVVRNsEGAtgvJxnLm2H+A5RQ93uIl+3632PZyl/skjfOn9Gvdwmlcw5aPUwimG+NT5
            EnNN036IaZePUuIcK533NVfal7/5yjWeot2z9ta1cAczHEf7I+3J0ws9Cgx0fsOFpmlfwKcWPuBQ
            73Oc4FHzBaZ8llq4q1mr5B2mOUCt815qYR8eB1hG2VJ7j35q4RofaH7IG+Xrf/PfJhfmwtfFYoIN
            AqxFUD6OMxcvkO+UfKfkOyXfKdsv/AYCHMLVkHAFWgAAAABJRU5ErkJggg==
            --===============1438169132528273974==--

        multipart/form-data
        -------------------

        As with creating new snippets, `multipart/form-data` can be used as an
        alternative to `multipart/related`. However, the inherently flat
        structure of form-data means that only basic, root-level properties
        can be returned, while nested elements like `links` are omitted:

            $ curl -H "Accept: multipart/form-data" https://api.bitbucket.org/2.0/snippets/evzijst/kypj

        Response:

            HTTP/1.1 200 OK
            Content-Length: 951
            Content-Type: multipart/form-data; boundary=----------------------------63a4b224c59f

            ------------------------------63a4b224c59f
            Content-Disposition: form-data; name="title"
            Content-Type: text/plain; charset="utf-8"

            My snippet
            ------------------------------63a4b224c59f--
            Content-Disposition: attachment; name="file"; filename="foo.txt"
            Content-Type: text/plain

            foo

            ------------------------------63a4b224c59f
            Content-Disposition: attachment; name="file"; filename="image.png"
            Content-Transfer-Encoding: base64
            Content-Type: application/octet-stream

            iVBORw0KGgoAAAANSUhEUgAAABQAAAAoCAYAAAD+MdrbAAABD0lEQVR4Ae3VMUoDQRTG8ccUaW2m
            TKONFxArJYJamCvkCnZTaa+VnQdJSBFl2SMsLFrEWNjZBZs0JgiL/+KrhhVmJRbCLPx4O+/DT2TB
            cbblJxf+UWFVVRNsEGAtgvJxnLm2H+A5RQ93uIl+3632PZyl/skjfOn9Gvdwmlcw5aPUwimG+NT5
            EnNN036IaZePUuIcK533NVfal7/5yjWeot2z9ta1cAczHEf7I+3J0ws9Cgx0fsOFpmlfwKcWPuBQ
            73Oc4FHzBaZ8llq4q1mr5B2mOUCt815qYR8eB1hG2VJ7j35q4RofaH7IG+Xrf/PfJhfmwtfFYoIN
            AqxFUD6OMxcvkO+UfKfkOyXfKdsv/AYCHMLVkHAFWgAAAABJRU5ErkJggg==
            ------------------------------5957323a6b76--
      operationId: getSnippetsUsernameEncoded
      x-api-path-slug: snippetsusernameencoded-id-get
      parameters:
      - in: path
        name: encoded_id
        description: The snippets id
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
    parameters:
      summary: Parameters Snippets Username Encoded
      description: Parameters snippets username encoded
      operationId: parametersSnippetsUsernameEncoded
      x-api-path-slug: snippetsusernameencoded-id-parameters
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
    put:
      summary: Update Snippets Username Encoded
      description: |-
        Used to update a snippet. Use this to add and delete files and to
        change a snippet's title.

        To update a snippet, one can either PUT a full snapshot, or only the
        parts that need to be changed.

        The contract for PUT on this API is that properties missing from the
        request remain untouched so that snippets can be efficiently
        manipulated with differential payloads.

        To delete a property (e.g. the title, or a file), include its name in
        the request, but omit its value (use `null`).

        As in Git, explicit renaming of files is not supported. Instead, to
        rename a file, delete it and add it again under another name. This can
        be done atomically in a single request. Rename detection is left to
        the SCM.

        PUT supports three different content types for both request and
        response bodies:

        * `application/json`
        * `multipart/related`
        * `multipart/form-data`

        The content type used for the request body can be different than that
        used for the response. Content types are specified using standard HTTP
        headers.

        Use the `Content-Type` and `Accept` headers to select the desired
        request and response format.


        application/json
        ----------------

        As with creation and retrieval, the content type determines what
        properties can be manipulated. `application/json` does not support
        file contents and is therefore limited to a snippet's meta data.

        To update the title, without changing any of its files:

            $ curl -X POST -H "Content-Type: application/json" https://api.bitbucket.org/2.0/snippets/evzijst/kypj             -d '{"title": "Updated title"}'


        To delete the title:

            $ curl -X POST -H "Content-Type: application/json" https://api.bitbucket.org/2.0/snippets/evzijst/kypj             -d '{"title": null}'

        Not all parts of a snippet can be manipulated. The owner and creator
        for instance are immutable.


        multipart/related
        -----------------

        `multipart/related` can be used to manipulate all of a snippet's
        properties. The body is identical to a POST. properties omitted from
        the request are left unchanged. Since the `start` part contains JSON,
        the mechanism for manipulating the snippet's meta data is identical
        to `application/json` requests.

        To update one of a snippet's file contents, while also changing its
        title:

            PUT /2.0/snippets/evzijst/kypj HTTP/1.1
            Content-Length: 288
            Content-Type: multipart/related; start="snippet"; boundary="===============1438169132528273974=="
            MIME-Version: 1.0

            --===============1438169132528273974==
            Content-Type: application/json; charset="utf-8"
            MIME-Version: 1.0
            Content-ID: snippet

            {
              "title": "My updated snippet",
              "files": {
                  "foo.txt": {}
                }
            }

            --===============1438169132528273974==
            Content-Type: text/plain; charset="us-ascii"
            MIME-Version: 1.0
            Content-Transfer-Encoding: 7bit
            Content-ID: "foo.txt"
            Content-Disposition: attachment; filename="foo.txt"

            Updated file contents.

            --===============1438169132528273974==--

        Here only the parts that are changed are included in the body. The
        other files remain untouched.

        Note the use of the `files` list in the JSON part. This list contains
        the files that are being manipulated. This list should have
        corresponding multiparts in the request that contain the new contents
        of these files.

        If a filename in the `files` list does not have a corresponding part,
        it will be deleted from the snippet, as shown below:

            PUT /2.0/snippets/evzijst/kypj HTTP/1.1
            Content-Length: 188
            Content-Type: multipart/related; start="snippet"; boundary="===============1438169132528273974=="
            MIME-Version: 1.0

            --===============1438169132528273974==
            Content-Type: application/json; charset="utf-8"
            MIME-Version: 1.0
            Content-ID: snippet

            {
              "files": {
                "image.png": {}
              }
            }

            --===============1438169132528273974==--

        To simulate a rename, delete a file and add the same file under
        another name:

            PUT /2.0/snippets/evzijst/kypj HTTP/1.1
            Content-Length: 212
            Content-Type: multipart/related; start="snippet"; boundary="===============1438169132528273974=="
            MIME-Version: 1.0

            --===============1438169132528273974==
            Content-Type: application/json; charset="utf-8"
            MIME-Version: 1.0
            Content-ID: snippet

            {
                "files": {
                  "foo.txt": {},
                  "bar.txt": {}
                }
            }

            --===============1438169132528273974==
            Content-Type: text/plain; charset="us-ascii"
            MIME-Version: 1.0
            Content-Transfer-Encoding: 7bit
            Content-ID: "bar.txt"
            Content-Disposition: attachment; filename="bar.txt"

            foo

            --===============1438169132528273974==--


        multipart/form-data
        -----------------

        Again, one can also use `multipart/form-data` to manipulate file
        contents and meta data atomically.

            $ curl -X PUT http://localhost:12345/2.0/snippets/evzijst/kypj             -F title="My updated snippet" -F file=@foo.txt

            PUT /2.0/snippets/evzijst/kypj HTTP/1.1
            Content-Length: 351
            Content-Type: multipart/form-data; boundary=----------------------------63a4b224c59f

            ------------------------------63a4b224c59f
            Content-Disposition: form-data; name="file"; filename="foo.txt"
            Content-Type: text/plain

            foo

            ------------------------------63a4b224c59f
            Content-Disposition: form-data; name="title"

            My updated snippet
            ------------------------------63a4b224c59f

        To delete a file, omit its contents while including its name in the
        `files` field:

            $ curl -X PUT https://api.bitbucket.org/2.0/snippets/evzijst/kypj -F files=image.png

            PUT /2.0/snippets/evzijst/kypj HTTP/1.1
            Content-Length: 149
            Content-Type: multipart/form-data; boundary=----------------------------ef8871065a86

            ------------------------------ef8871065a86
            Content-Disposition: form-data; name="files"

            image.png
            ------------------------------ef8871065a86--

        The explicit use of the `files` element in `multipart/related` and
        `multipart/form-data` is only required when deleting files.
        The default mode of operation is for file parts to be processed,
        regardless of whether or not they are listed in `files`, as a
        convenience to the client.
      operationId: putSnippetsUsernameEncoded
      x-api-path-slug: snippetsusernameencoded-id-put
      parameters:
      - in: path
        name: encoded_id
        description: The snippets id
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
  /snippets/{username}/{encoded_id}/comments:
    get:
      summary: Get Snippets Username Encoded  Comments
      description: |-
        Used to retrieve a paginated list of all comments for a specific
        snippet.

        This resource works identical to commit and pull request comments.

        The default sorting is oldest to newest and can be overridden with
        the `sort` query parameter.
      operationId: getSnippetsUsernameEncodedComments
      x-api-path-slug: snippetsusernameencoded-idcomments-get
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Comments
    parameters:
      summary: Parameters Snippets Username Encoded  Comments
      description: Parameters snippets username encoded  comments
      operationId: parametersSnippetsUsernameEncodedComments
      x-api-path-slug: snippetsusernameencoded-idcomments-parameters
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Comments
    post:
      summary: Add Snippets Username Encoded  Comments
      description: |-
        Creates a new comment.

        The only required field in the body is `content.raw`.

        To create a threaded reply to an existing comment, include `parent.id`.
      operationId: postSnippetsUsernameEncodedComments
      x-api-path-slug: snippetsusernameencoded-idcomments-post
      parameters:
      - in: body
        name: _body
        description: The contents of the new comment
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Comments
  /snippets/{username}/{encoded_id}/comments/{comment_id}:
    delete:
      summary: Delete Snippets Username Encoded  Comments Comment
      description: |-
        Deletes a snippet comment.

        Comments can only be removed by their author.
      operationId: deleteSnippetsUsernameEncodedCommentsComment
      x-api-path-slug: snippetsusernameencoded-idcommentscomment-id-delete
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Comments
      - Comment
    get:
      summary: Get Snippets Username Encoded  Comments Comment
      description: Get snippets username encoded  comments comment
      operationId: getSnippetsUsernameEncodedCommentsComment
      x-api-path-slug: snippetsusernameencoded-idcommentscomment-id-get
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Comments
      - Comment
    parameters:
      summary: Parameters Snippets Username Encoded  Comments Comment
      description: Parameters snippets username encoded  comments comment
      operationId: parametersSnippetsUsernameEncodedCommentsComment
      x-api-path-slug: snippetsusernameencoded-idcommentscomment-id-parameters
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Comments
      - Comment
    put:
      summary: Update Snippets Username Encoded  Comments Comment
      description: |-
        Updates a comment.

        Comments can only be updated by their author.
      operationId: putSnippetsUsernameEncodedCommentsComment
      x-api-path-slug: snippetsusernameencoded-idcommentscomment-id-put
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Comments
      - Comment
  /snippets/{username}/{encoded_id}/commits:
    get:
      summary: Get Snippets Username Encoded  Commits
      description: Returns the changes (commits) made on this snippet.
      operationId: getSnippetsUsernameEncodedCommits
      x-api-path-slug: snippetsusernameencoded-idcommits-get
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Commits
    parameters:
      summary: Parameters Snippets Username Encoded  Commits
      description: Parameters snippets username encoded  commits
      operationId: parametersSnippetsUsernameEncodedCommits
      x-api-path-slug: snippetsusernameencoded-idcommits-parameters
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Username
      - Encoded
      - ""
      - Commits
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---