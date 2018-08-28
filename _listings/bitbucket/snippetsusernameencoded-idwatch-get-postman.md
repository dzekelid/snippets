{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Watch",
    "_postman_id": "93b20d00-9b34-44ff-81bf-93ac2524a2f2",
    "description": "Used to check if the current user is watching a specific snippet.\n\nReturns 204 (No Content) if the user is watching the snippet and 404 if\nnot.\n\nHitting this endpoint anonymously always returns a 404.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "63ad17b5-e234-4625-8dc1-b66b1ebbffea",
          "name": "getSnippetsUsernameEncodedWatch",
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
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Used to check if the current user is watching a specific snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "0eb6a8ff-7448-4560-87e0-9a324c2ce989"
            }
          ]
        }
      ]
    }
  ]
}