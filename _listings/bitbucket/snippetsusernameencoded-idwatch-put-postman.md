{
  "info": {
    "name": "Bitbucket Update Snippets Username Encoded  Watch",
    "_postman_id": "79d697b8-29e2-49c7-934f-756ee511faa4",
    "description": "Used to start watching a specific snippet. Returns 204 (No Content).",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "230d1ca1-b54a-4d5b-be23-6338f4f120ce",
          "name": "putSnippetsUsernameEncodedWatch",
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
            "method": "PUT",
            "body": {
              "mode": "raw"
            },
            "description": "Used to start watching a specific snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "c046e2e7-4600-41f0-ac02-fe4f3c8d56ca"
            }
          ]
        }
      ]
    }
  ]
}