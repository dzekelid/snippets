{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Node  Files Path",
    "_postman_id": "5f5449d8-c213-410b-ac65-efe8f91f8bf4",
    "description": "Retrieves the raw contents of a specific file in the snippet. The\n`Content-Disposition` header will be \"attachment\" to avoid issues with\nmalevolent executable files.\n\nThe file's mime type is derived from its filename and returned in the\n`Content-Type` header.\n\nNote that for text files, no character encoding is included as part of\nthe content type.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "2e9aa81a-f680-431c-bdd4-cb36b290b781",
          "name": "getSnippetsUsernameEncodedNodeFilesPath",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/:node_id/files/:path"
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
                  "id": "node_id",
                  "value": "node_id",
                  "type": "string"
                },
                {
                  "id": "path",
                  "value": "path",
                  "type": "string"
                }
              ]
            },
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Retrieves the raw contents of a specific file in the snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "72bdd631-ea5c-4fa5-8f58-1139c71e6064"
            }
          ]
        }
      ]
    }
  ]
}