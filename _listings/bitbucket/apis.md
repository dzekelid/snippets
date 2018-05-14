---
name: Bitbucket
description: Code against the Bitbucket API to automate simple tasks, embed Bitbucket
  data into your own site, build mobile or desktop apps, or even add custom UI add-ons
  into Bitbucket itself using the Connect framework.
image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/bitbucket-logo.png
x-kinRank: "8"
x-alexaRank: ""
tags:
- Stack Network
- Imports
- Developers
created: "2018-03-24"
modified: "2018-03-24"
url: https://raw.githubusercontent.com/streamdata-gallery-topics/snippets/master/_listings/bitbucket/apis.yaml
specificationVersion: "0.14"
apis:
- name: Bitbucket
  description: Code against the Bitbucket API to automate simple tasks, embed Bitbucket
    data into your own site, build mobile or desktop apps, or even add custom UI add-ons
    into Bitbucket itself using the Connect framework
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/bitbucket-logo.png
  humanURL: ""
  baseURL: https://api.bitbucket.org//2.0
  tags: Snippets
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/snippets/master/_listings/bitbucket/snippets-username-encoded-id-revision-patch-parameters.md
- name: Bitbucket Add Snippets
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/bitbucket-logo.png
  humanURL: https://bitbucket.org/
  baseURL: https://api.bitbucket.org//2.0
  tags: Snippets
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/snippets/master/_listings/bitbucket/snippets-post.md
x-common:
- type: x-developer
  url: https://developer.atlassian.com/cloud/bitbucket/
- type: x-documentation
  url: https://confluence.atlassian.com/bitbucket/bitbucket-cloud-documentation-221448814.html?_ga=2.77295890.629375793.1519179030-1077111323.1516485126
- type: x-status
  url: https://status.bitbucket.org/?_ga=2.76365714.629375793.1519179030-1077111323.1516485126
- type: x-support
  url: https://support.atlassian.com/bitbucket-cloud/
- type: x-terms-of-service
  url: https://www.atlassian.com/legal/customer-agreement?_ga=2.76365714.629375793.1519179030-1077111323.1516485126
- type: x-twitter
  url: https://twitter.com/bitbucket
- type: x-website
  url: https://bitbucket.org/
- type: x-developer
  url: https://developer.atlassian.com/cloud/bitbucket/
- type: x-documentation
  url: https://confluence.atlassian.com/bitbucket/bitbucket-cloud-documentation-221448814.html?_ga=2.77295890.629375793.1519179030-1077111323.1516485126
- type: x-status
  url: https://status.bitbucket.org/?_ga=2.76365714.629375793.1519179030-1077111323.1516485126
- type: x-support
  url: https://support.atlassian.com/bitbucket-cloud/
- type: x-terms-of-service
  url: https://www.atlassian.com/legal/customer-agreement?_ga=2.76365714.629375793.1519179030-1077111323.1516485126
- type: x-twitter
  url: https://twitter.com/bitbucket
- type: x-website
  url: https://bitbucket.org/
include: []
maintainers:
- FN: Kin Lane
  x-twitter: apievangelist
  email: info@apievangelist.com
---