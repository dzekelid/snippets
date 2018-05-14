---
swagger: "2.0"
info:
  title: Bitbucket Update Snippets Username Encoded
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
  /snippets/{username}/{encoded_id}:
    put:
      summary: Update Snippets Username Encoded
      description: Used to update a snippet
      operationId: putSnippetsUsernameEncoded
      parameters:
      - in: path
        name: encoded_id
        description: The snippet's id
      responses:
        200:
          description: OK
      tags:
      - snippets
      - username
      - encoded
definitions:
  error:
    properties:
      error:
        description: This is a default description.
        type: parameters
      type:
        description: This is a default description.
        type: parameters
  hook_event:
    properties:
      category:
        description: This is a default description.
        type: parameters
      description:
        description: This is a default description.
        type: parameters
      event:
        description: This is a default description.
        type: parameters
      label:
        description: This is a default description.
        type: parameters
  object:
    properties:
      type:
        description: This is a default description.
        type: parameters
  page:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
  paginated_branchrestrictions:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_commitstatuses:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_components:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_hook_events:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_issue_attachments:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_issues:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_milestones:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_pipeline_known_hosts:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_pipeline_steps:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_pipeline_variables:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_pipelines:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_projects:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_pullrequests:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_repositories:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_snippet_comments:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_snippet_commit:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_snippets:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_teams:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_users:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_versions:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  paginated_webhook_subscriptions:
    properties:
      next:
        description: This is a default description.
        type: parameters
      page:
        description: This is a default description.
        type: parameters
      pagelen:
        description: This is a default description.
        type: parameters
      previous:
        description: This is a default description.
        type: parameters
      size:
        description: This is a default description.
        type: parameters
      values:
        description: This is a default description.
        type: parameters
  pipeline_command:
    properties:
      command:
        description: This is a default description.
        type: parameters
      name:
        description: This is a default description.
        type: parameters
  pipeline_image:
    properties:
      email:
        description: This is a default description.
        type: parameters
      name:
        description: This is a default description.
        type: parameters
      password:
        description: This is a default description.
        type: parameters
      username:
        description: This is a default description.
        type: parameters
  pipeline_log_range:
    properties:
      first_byte_position:
        description: This is a default description.
        type: parameters
      last_byte_position:
        description: This is a default description.
        type: parameters
  pullrequest_endpoint:
    properties:
      branch:
        description: This is a default description.
        type: parameters
      commit:
        description: This is a default description.
        type: parameters
  pullrequest_merge_parameters:
    properties:
      close_source_branch:
        description: This is a default description.
        type: parameters
      merge_strategy:
        description: This is a default description.
        type: parameters
      message:
        description: This is a default description.
        type: parameters
      type:
        description: This is a default description.
        type: parameters
  subject_types:
    properties:
      repository:
        description: This is a default description.
        type: parameters
      team:
        description: This is a default description.
        type: parameters
      user:
        description: This is a default description.
        type: parameters
  tag:
    properties:
      date:
        description: This is a default description.
        type: parameters
      links:
        description: This is a default description.
        type: parameters
      message:
        description: This is a default description.
        type: parameters
      name:
        description: This is a default description.
        type: parameters
      type:
        description: This is a default description.
        type: parameters
x-collection-name: Bitbucket
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