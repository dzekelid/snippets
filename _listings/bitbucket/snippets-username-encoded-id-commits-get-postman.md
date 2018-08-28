{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Commits",
    "_postman_id": "029e7f5a-4c00-4376-a60a-0682ec7b27a9",
    "description": "Returns the changes (commits) made on this snippet.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "ecc10aa6-0dae-434a-a96c-5e263998d5b1",
          "name": "getSnippetsUsernameEncodedCommits",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/commits"
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
                }
              ]
            },
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Returns the changes (commits) made on this snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "dc77cbba-2ec3-438e-be61-a1ce99637cc7"
            }
          ]
        }
      ]
    }
  ]
}