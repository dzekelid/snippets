{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Node",
    "_postman_id": "84263f5f-0659-4da5-835f-b69afe78eab8",
    "description": "Identical to `GET /snippets/encoded_id`, except that this endpoint\ncan be used to retrieve the contents of the snippet as it was at an\nolder revision, while `/snippets/encoded_id` always returns the\nsnippet's current revision.\n\nNote that only the snippet's file contents are versioned, not its\nmeta data properties like the title.\n\nOther than that, the two endpoints are identical in behavior.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "85b305e1-361d-48fb-ae3b-360a3ed08722",
          "name": "getSnippetsUsernameEncodedNode",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/:node_id"
              ],
              "variable": [
                {
                  "id": "encoded_id",
                  "value": "{}",
                  "type": "string"
                },
                {
                  "id": "node_id",
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
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Identical to `GET /snippets/encoded_id`, except that this endpoint\ncan be used to retrieve the contents of the snippet as it was at an\nolder revision, while `/snippets/encoded_id` always returns the\nsnippet's current revision"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "20b0fb50-0d69-46a2-bce1-7cf516ac6e75"
            }
          ]
        }
      ]
    }
  ]
}