{
  "info": {
    "name": "Bitbucket Delete Snippets Username Encoded  Node",
    "_postman_id": "19677ed7-3d2c-40fc-9a4c-bcc7ecec3d49",
    "description": "Deletes the snippet.\n\nNote that this only works for versioned URLs that point to the latest\ncommit of the snippet. Pointing to an older commit results in a 405\nstatus code.\n\nTo delete a snippet, regardless of whether or not concurrent changes\nare being made to it, use `DELETE /snippets/{encoded_id}` instead.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "e3c1f063-6f62-4a0c-bc5b-39c311862fa5",
          "name": "deleteSnippetsUsernameEncodedNode",
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
                  "id": "username",
                  "value": "username",
                  "type": "string"
                },
                {
                  "id": "node_id",
                  "value": "node_id",
                  "type": "string"
                }
              ]
            },
            "method": "DELETE",
            "body": {
              "mode": "raw"
            },
            "description": "Deletes the snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "7404ac49-c10c-45b3-8c08-8ddcadbcae31"
            }
          ]
        }
      ]
    }
  ]
}