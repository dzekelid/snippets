{
  "info": {
    "name": "Bitbucket Get Snippets",
    "_postman_id": "070e44c3-ad30-47d0-ab6f-1fb862779f76",
    "description": "Returns all snippets. Like pull requests, repositories and teams, the\nfull set of snippets is defined by what the current user has access to.\n\nThis includes all snippets owned by the current user, but also all snippets\nowned by any of the teams the user is a member of, or snippets by other\nusers that the current user is either watching or has collaborated on (for\ninstance by commenting on it).\n\nTo limit the set of returned snippets, apply the\n`?role=[owner|contributor|member]` query parameter where the roles are\ndefined as follows:\n\n* `owner`: all snippets owned by the current user\n* `contributor`: all snippets owned by, or watched by the current user\n* `member`: owned by the user, their teams, or watched by the current user\n\nWhen no role is specified, all public snippets are returned, as well as all\nprivately owned snippets watched or commented on.\n\nThe returned response is a normal paginated JSON list. This endpoint\nonly supports `application/json` responses and no\n`multipart/form-data` or `multipart/related`. As a result, it is not\npossible to include the file contents.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "92650a22-35b6-4c37-801a-c6d64a89722e",
          "name": "getSnippets",
          "request": {
            "url": "http://api.bitbucket.org/2.0/snippets?role=%7B%7D",
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Returns all snippets"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "7513fe6f-f6ec-4aed-bbe7-a13e2d0a1200"
            }
          ]
        }
      ]
    }
  ]
}