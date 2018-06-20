{
  "info": {
    "name": "Bitbucket Update Snippets Username Encoded  Comments Comment",
    "_postman_id": "cdd4b160-95f6-4d22-8bd8-f13413b49999",
    "description": "Updates a comment.\n\nComments can only be updated by their author.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "fe781ef9-4e25-4756-ad85-df2b18766a5e",
          "name": "putSnippetsUsernameEncodedCommentsComment",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/comments/:comment_id"
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
                },
                {
                  "id": "comment_id",
                  "value": "comment_id",
                  "type": "string"
                }
              ]
            },
            "method": "PUT",
            "body": {
              "mode": "raw"
            },
            "description": "Updates a comment"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "aff418a1-a7eb-4ed6-8019-c37477d4e9c8"
            }
          ]
        }
      ]
    }
  ]
}