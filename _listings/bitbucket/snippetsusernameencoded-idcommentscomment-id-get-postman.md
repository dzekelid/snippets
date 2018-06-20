{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Comments Comment",
    "_postman_id": "03e2f1fa-1035-49fc-96e5-89ea2899bbce",
    "description": "Get snippets username encoded  comments comment",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "02f27f62-5db8-4a3b-b00b-8d41e16a3bf8",
          "name": "getSnippetsUsernameEncodedCommentsComment",
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
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Get snippets username encoded  comments comment"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "b319d991-08b1-42dc-b8a8-bac8dbbe4f4e"
            }
          ]
        }
      ]
    }
  ]
}