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
- name: Bitbucket Get Snippets
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/bitbucket-logo.png
  humanURL: https://bitbucket.org/
  baseURL: https://api.bitbucket.org//2.0
  tags: Snippets
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/snippets/master/_listings/bitbucket/snippets-get.md
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-topics/snippets/master/_listings/bitbucket/snippets-get-postman.md
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