---
swagger: "2.0"
x-collection-name: GitLab
x-complete: 0
info:
  title: GitLab Get Projects Snippets Snippet Notes Note Award Emoji Award
  version: 1.0.0
  description: Get projects snippets snippet notes note award emoji award.
host: localhost:3000
basePath: /api
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /v3/projects/{id}/snippets/{snippet_id}/award_emoji:
    get:
      summary: Get Projects Snippets Snippet Award Emoji
      description: Get projects snippets snippet award emoji.
      operationId: getV3ProjectsIdSnippetsSnippetIdAwardEmoji
      x-api-path-slug: v3projectsidsnippetssnippet-idaward-emoji-get
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: query
        name: page
        description: Current page number
      - in: query
        name: per_page
        description: Number of items per page
      - in: path
        name: snippet_id
        description: The ID of an Issue, Merge Request or Snippet
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Award
      - Emoji
    post:
      summary: Post Projects Snippets Snippet Award Emoji
      description: Post projects snippets snippet award emoji.
      operationId: postV3ProjectsIdSnippetsSnippetIdAwardEmoji
      x-api-path-slug: v3projectsidsnippetssnippet-idaward-emoji-post
      parameters:
      - in: path
        name: id
      - in: formData
        name: name
        description: The name of a award_emoji (without colons)
      - in: path
        name: snippet_id
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Award
      - Emoji
  /v3/projects/{id}/snippets/{snippet_id}/award_emoji/{award_id}:
    get:
      summary: Get Projects Snippets Snippet Award Emoji Award
      description: Get projects snippets snippet award emoji award.
      operationId: getV3ProjectsIdSnippetsSnippetIdAwardEmojiAwardId
      x-api-path-slug: v3projectsidsnippetssnippet-idaward-emojiaward-id-get
      parameters:
      - in: path
        name: award_id
        description: The ID of the award
      - in: path
        name: id
      - in: path
        name: snippet_id
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Award
      - Emoji
      - Award
    delete:
      summary: Delete Projects Snippets Snippet Award Emoji Award
      description: Delete projects snippets snippet award emoji award.
      operationId: deleteV3ProjectsIdSnippetsSnippetIdAwardEmojiAwardId
      x-api-path-slug: v3projectsidsnippetssnippet-idaward-emojiaward-id-delete
      parameters:
      - in: path
        name: award_id
        description: The ID of an award emoji
      - in: path
        name: id
      - in: path
        name: snippet_id
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Award
      - Emoji
      - Award
  /v3/projects/{id}/snippets/{snippet_id}/notes/{note_id}/award_emoji:
    get:
      summary: Get Projects Snippets Snippet Notes Note Award Emoji
      description: Get projects snippets snippet notes note award emoji.
      operationId: getV3ProjectsIdSnippetsSnippetIdNotesNoteIdAwardEmoji
      x-api-path-slug: v3projectsidsnippetssnippet-idnotesnote-idaward-emoji-get
      parameters:
      - in: path
        name: id
      - in: path
        name: note_id
      - in: query
        name: page
        description: Current page number
      - in: query
        name: per_page
        description: Number of items per page
      - in: path
        name: snippet_id
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Notes
      - Note
      - Award
      - Emoji
    post:
      summary: Post Projects Snippets Snippet Notes Note Award Emoji
      description: Post projects snippets snippet notes note award emoji.
      operationId: postV3ProjectsIdSnippetsSnippetIdNotesNoteIdAwardEmoji
      x-api-path-slug: v3projectsidsnippetssnippet-idnotesnote-idaward-emoji-post
      parameters:
      - in: path
        name: id
      - in: formData
        name: name
        description: The name of a award_emoji (without colons)
      - in: path
        name: note_id
      - in: path
        name: snippet_id
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Notes
      - Note
      - Award
      - Emoji
  /v3/projects/{id}/snippets/{snippet_id}/notes/{note_id}/award_emoji/{award_id}:
    get:
      summary: Get Projects Snippets Snippet Notes Note Award Emoji Award
      description: Get projects snippets snippet notes note award emoji award.
      operationId: getV3ProjectsIdSnippetsSnippetIdNotesNoteIdAwardEmojiAwardId
      x-api-path-slug: v3projectsidsnippetssnippet-idnotesnote-idaward-emojiaward-id-get
      parameters:
      - in: path
        name: award_id
        description: The ID of the award
      - in: path
        name: id
      - in: path
        name: note_id
      - in: path
        name: snippet_id
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Notes
      - Note
      - Award
      - Emoji
      - Award
    delete:
      summary: Delete Projects Snippets Snippet Notes Note Award Emoji Award
      description: Delete projects snippets snippet notes note award emoji award.
      operationId: deleteV3ProjectsIdSnippetsSnippetIdNotesNoteIdAwardEmojiAwardId
      x-api-path-slug: v3projectsidsnippetssnippet-idnotesnote-idaward-emojiaward-id-delete
      parameters:
      - in: path
        name: award_id
        description: The ID of an award emoji
      - in: path
        name: id
      - in: path
        name: note_id
      - in: path
        name: snippet_id
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Notes
      - Note
      - Award
      - Emoji
      - Award
  /v3/projects/{id}/snippets/{noteable_id}/notes:
    get:
      summary: Get Projects Snippets Noteable Notes
      description: Get a list of project +noteable+ notes
      operationId: getV3ProjectsIdSnippetsNoteableIdNotes
      x-api-path-slug: v3projectsidsnippetsnoteable-idnotes-get
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: noteable_id
        description: The ID of the noteable
      - in: query
        name: page
        description: Current page number
      - in: query
        name: per_page
        description: Number of items per page
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Noteable
      - Notes
    post:
      summary: Post Projects Snippets Noteable Notes
      description: Post projects snippets noteable notes.
      operationId: postV3ProjectsIdSnippetsNoteableIdNotes
      x-api-path-slug: v3projectsidsnippetsnoteable-idnotes-post
      parameters:
      - in: formData
        name: body
        description: The content of a note
      - in: formData
        name: created_at
        description: The creation date of the note
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: noteable_id
        description: The ID of the noteable
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Noteable
      - Notes
  /v3/projects/{id}/snippets/{noteable_id}/notes/{note_id}:
    get:
      summary: Get Projects Snippets Noteable Notes Note
      description: Get projects snippets noteable notes note.
      operationId: getV3ProjectsIdSnippetsNoteableIdNotesNoteId
      x-api-path-slug: v3projectsidsnippetsnoteable-idnotesnote-id-get
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: noteable_id
        description: The ID of the noteable
      - in: path
        name: note_id
        description: The ID of a note
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Noteable
      - Notes
      - Note
    put:
      summary: Put Projects Snippets Noteable Notes Note
      description: Put projects snippets noteable notes note.
      operationId: putV3ProjectsIdSnippetsNoteableIdNotesNoteId
      x-api-path-slug: v3projectsidsnippetsnoteable-idnotesnote-id-put
      parameters:
      - in: formData
        name: body
        description: The content of a note
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: noteable_id
        description: The ID of the noteable
      - in: path
        name: note_id
        description: The ID of a note
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Noteable
      - Notes
      - Note
    delete:
      summary: Delete Projects Snippets Noteable Notes Note
      description: Delete projects snippets noteable notes note.
      operationId: deleteV3ProjectsIdSnippetsNoteableIdNotesNoteId
      x-api-path-slug: v3projectsidsnippetsnoteable-idnotesnote-id-delete
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: noteable_id
        description: The ID of the noteable
      - in: path
        name: note_id
        description: The ID of a note
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Noteable
      - Notes
      - Note
  /v3/projects/{id}/snippets:
    get:
      summary: Get Projects Snippets
      description: Get all project snippets
      operationId: getV3ProjectsIdSnippets
      x-api-path-slug: v3projectsidsnippets-get
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: query
        name: page
        description: Current page number
      - in: query
        name: per_page
        description: Number of items per page
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
    post:
      summary: Post Projects Snippets
      description: Create a new project snippet
      operationId: postV3ProjectsIdSnippets
      x-api-path-slug: v3projectsidsnippets-post
      parameters:
      - in: formData
        name: code
        description: The content of the snippet
      - in: formData
        name: file_name
        description: The file name of the snippet
      - in: path
        name: id
        description: The ID of a project
      - in: formData
        name: title
        description: The title of the snippet
      - in: formData
        name: visibility_level
        description: The visibility level of the snippet
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
  /v3/projects/{id}/snippets/{snippet_id}:
    get:
      summary: Get Projects Snippets Snippet
      description: Get projects snippets snippet.
      operationId: getV3ProjectsIdSnippetsSnippetId
      x-api-path-slug: v3projectsidsnippetssnippet-id-get
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: snippet_id
        description: The ID of a project snippet
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
    put:
      summary: Put Projects Snippets Snippet
      description: Update an existing project snippet
      operationId: putV3ProjectsIdSnippetsSnippetId
      x-api-path-slug: v3projectsidsnippetssnippet-id-put
      parameters:
      - in: formData
        name: code
        description: The content of the snippet
      - in: formData
        name: file_name
        description: The file name of the snippet
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: snippet_id
        description: The ID of a project snippet
      - in: formData
        name: title
        description: The title of the snippet
      - in: formData
        name: visibility_level
        description: The visibility level of the snippet
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
    delete:
      summary: Delete Projects Snippets Snippet
      description: Delete projects snippets snippet.
      operationId: deleteV3ProjectsIdSnippetsSnippetId
      x-api-path-slug: v3projectsidsnippetssnippet-id-delete
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: snippet_id
        description: The ID of a project snippet
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
  /v3/projects/{id}/snippets/{snippet_id}/raw:
    get:
      summary: Get Projects Snippets Snippet Raw
      description: Get projects snippets snippet raw.
      operationId: getV3ProjectsIdSnippetsSnippetIdRaw
      x-api-path-slug: v3projectsidsnippetssnippet-idraw-get
      parameters:
      - in: path
        name: id
        description: The ID of a project
      - in: path
        name: snippet_id
        description: The ID of a project snippet
      responses:
        200:
          description: OK
      tags:
      - Projects
      - Snippets
      - Snippet
      - Raw
  /v3/snippets:
    get:
      summary: Get Snippets
      description: This feature was introduced in GitLab 8.15.
      operationId: getV3Snippets
      x-api-path-slug: v3snippets-get
      parameters:
      - in: query
        name: page
        description: Current page number
      - in: query
        name: per_page
        description: Number of items per page
      responses:
        200:
          description: OK
      tags:
      - Snippets
    post:
      summary: Post Snippets
      description: This feature was introduced in GitLab 8.15.
      operationId: postV3Snippets
      x-api-path-slug: v3snippets-post
      parameters:
      - in: formData
        name: content
        description: The content of a snippet
      - in: formData
        name: file_name
        description: The name of a snippet file
      - in: formData
        name: title
        description: The title of a snippet
      - in: formData
        name: visibility_level
        description: The visibility level of the snippet
      responses:
        200:
          description: OK
      tags:
      - Snippets
  /v3/snippets/public:
    get:
      summary: Get Snippets Public
      description: This feature was introduced in GitLab 8.15.
      operationId: getV3SnippetsPublic
      x-api-path-slug: v3snippetspublic-get
      parameters:
      - in: query
        name: page
        description: Current page number
      - in: query
        name: per_page
        description: Number of items per page
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Public
  /v3/snippets/{id}:
    get:
      summary: Get Snippets
      description: This feature was introduced in GitLab 8.15.
      operationId: getV3SnippetsId
      x-api-path-slug: v3snippetsid-get
      parameters:
      - in: path
        name: id
        description: The ID of a snippet
      responses:
        200:
          description: OK
      tags:
      - Snippets
    put:
      summary: Put Snippets
      description: This feature was introduced in GitLab 8.15.
      operationId: putV3SnippetsId
      x-api-path-slug: v3snippetsid-put
      parameters:
      - in: formData
        name: content
        description: The content of a snippet
      - in: formData
        name: file_name
        description: The name of a snippet file
      - in: path
        name: id
        description: The ID of a snippet
      - in: formData
        name: title
        description: The title of a snippet
      - in: formData
        name: visibility_level
        description: The visibility level of the snippet
      responses:
        200:
          description: OK
      tags:
      - Snippets
    delete:
      summary: Delete Snippets
      description: This feature was introduced in GitLab 8.15.
      operationId: deleteV3SnippetsId
      x-api-path-slug: v3snippetsid-delete
      parameters:
      - in: path
        name: id
        description: The ID of a snippet
      responses:
        200:
          description: OK
      tags:
      - Snippets
  /v3/snippets/{id}/raw:
    get:
      summary: Get Snippets Raw
      description: This feature was introduced in GitLab 8.15.
      operationId: getV3SnippetsIdRaw
      x-api-path-slug: v3snippetsidraw-get
      parameters:
      - in: path
        name: id
        description: The ID of a snippet
      responses:
        200:
          description: OK
      tags:
      - Snippets
      - Raw
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