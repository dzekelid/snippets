{
  "info": {
    "name": "Bitbucket Delete Snippets Username Encoded",
    "_postman_id": "9a59abd4-22c3-48ba-9890-62170d65a116",
    "description": "Deletes a snippet and returns an empty response.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "ec0d0d02-9568-4479-9bf4-7a05720636c7",
          "name": "deleteSnippetsUsernameEncoded",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id"
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
            "description": "Deletes a snippet and returns an empty response"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "b33a3c1d-4f18-410b-a002-c022a72a1d04"
            }
          ]
        }
      ]
    }
  ]
}