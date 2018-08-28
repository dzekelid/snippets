{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Commits Revision",
    "_postman_id": "f2c28bbc-cbb0-4c5a-851e-ef6d3c6927a5",
    "description": "Get snippets username encoded  commits revision",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "1107a8d3-5235-41e9-8b25-9c495cc568cf",
          "name": "getSnippetsUsernameEncodedCommitsRevision",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/commits/:revision"
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
                  "id": "revision",
                  "value": "revision",
                  "type": "string"
                }
              ]
            },
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Get snippets username encoded  commits revision"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "8e1b5321-eb18-4423-892f-0ccc008def67"
            }
          ]
        }
      ]
    }
  ]
}