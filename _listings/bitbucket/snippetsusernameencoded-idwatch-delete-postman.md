{
  "info": {
    "name": "Bitbucket Delete Snippets Username Encoded  Watch",
    "_postman_id": "a908af01-39bb-4acd-9c09-7b397124988c",
    "description": "Used to stop watching a specific snippet. Returns 204 (No Content)\nto indicate success.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "a063442b-7e75-4907-9105-4be4b32303aa",
          "name": "deleteSnippetsUsernameEncodedWatch",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/watch"
              ],
              "variable": [
                {
                  "id": "encoded_id",
                  "value": "{}",
                  "type": "string"
                },
                {
                  "id": "username",
                  "value": "username",
                  "type": "string"
                }
              ]
            },
            "method": "DELETE",
            "body": {
              "mode": "raw"
            },
            "description": "Used to stop watching a specific snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "eb86dda9-77d3-47b0-a5ea-0a019d599f5b"
            }
          ]
        }
      ]
    }
  ]
}