---
swagger: "2.0"
info:
  title: Bitbucket Get Snippets Username Encoded  Commits Revision
  description: Get snippets username encoded  commits revision
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
  /snippets/{username}/{encoded_id}/commits/{revision}:
    get:
      summary: Get Snippets Username Encoded  Commits Revision
      description: Get snippets username encoded  commits revision
      operationId: getSnippetsUsernameEncodedCommitsRevision
      responses:
        200:
          description: OK
      tags:
      - snippets
      - username
      - encoded
      - ""
      - commits
      - revision
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