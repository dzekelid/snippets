{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Watchers",
    "_postman_id": "eac9addd-63a4-4254-8c8d-b6a5cc040dcc",
    "description": "Returns a paginated list of all users watching a specific snippet.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "5f626844-c495-4d87-9333-7d8cc700b3e4",
          "name": "getSnippetsUsernameEncodedWatchers",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/watchers"
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
            "description": "Returns a paginated list of all users watching a specific snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "63d6959b-610d-4c21-856a-ecb3112cdccd"
            }
          ]
        }
      ]
    }
  ]
}