{
  "info": {
    "name": "Bitbucket Get Snippets Username",
    "_postman_id": "7dc16ec6-649a-469c-bf71-5c5931dad658",
    "description": "Identical to `/snippets`, except that the result is further filtered\nby the snippet owner and only those that are owned by `{username}` are\nreturned.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "6bc54be0-0fc8-4f53-8276-96692e19228c",
          "name": "getSnippetsUsername",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username"
              ],
              "query": [
                {
                  "key": "role",
                  "value": "%7B%7D",
                  "disabled": false
                }
              ],
              "variable": [
                {
                  "id": "username",
                  "value": "{}",
                  "type": "string"
                }
              ]
            },
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Identical to `/snippets`, except that the result is further filtered\nby the snippet owner and only those that are owned by `{username}` are\nreturned"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "130a01c5-b96a-4b4f-96ea-f54ca82c8203"
            }
          ]
        }
      ]
    }
  ]
}