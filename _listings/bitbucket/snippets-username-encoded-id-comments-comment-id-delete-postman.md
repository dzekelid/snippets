{
  "info": {
    "name": "Bitbucket Delete Snippets Username Encoded  Comments Comment",
    "_postman_id": "e4040688-0397-4b55-b031-e9bc02ae126b",
    "description": "Deletes a snippet comment.\n\nComments can only be removed by their author.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "358c21d5-bcca-4bb2-8809-968b2eff6309",
          "name": "deleteSnippetsUsernameEncodedCommentsComment",
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
            "method": "DELETE",
            "body": {
              "mode": "raw"
            },
            "description": "Deletes a snippet comment"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "19900669-f9c4-4a5b-ad64-da285c5a410f"
            }
          ]
        }
      ]
    }
  ]
}