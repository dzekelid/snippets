{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Comments",
    "_postman_id": "5fd145c6-ff2b-43f2-acc7-67d70717cdb9",
    "description": "Used to retrieve a paginated list of all comments for a specific\nsnippet.\n\nThis resource works identical to commit and pull request comments.\n\nThe default sorting is oldest to newest and can be overridden with\nthe `sort` query parameter.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "4e1f11ee-0d7b-40a0-83b9-ebd80434af28",
          "name": "getSnippetsUsernameEncodedComments",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/comments"
              ],
              "variable": [
                {
                  "id": "username",
                  "value": "username",
                  "type": "string"
                },
                {
                  "id": "encoded_id",
                  "value": "encoded_id",
                  "type": "string"
                }
              ]
            },
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Used to retrieve a paginated list of all comments for a specific\nsnippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "09ae8ec6-11b7-40b7-aec3-27688a75a025"
            }
          ]
        }
      ]
    }
  ]
}