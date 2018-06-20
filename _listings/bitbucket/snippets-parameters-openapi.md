---
swagger: "2.0"
x-collection-name: Bitbucket
x-complete: 0
info:
  title: Bitbucket Parameters Snippets
  description: Parameters snippets
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