{
  "info": {
    "name": "Bitbucket Update Snippets Username Encoded  Node",
    "_postman_id": "2e486712-d0cc-46a4-8fec-014204a9d3b2",
    "description": "Identical to `UPDATE /snippets/encoded_id`, except that this endpoint\ntakes an explicit commit revision. Only the snippet's \"HEAD\"/\"tip\"\n(most recent) version can be updated and requests on all other,\nolder revisions fail by returning a 405 status.\n\nUsage of this endpoint over the unrestricted `/snippets/encoded_id`\ncould be desired if the caller wants to be sure no concurrent\nmodifications have taken place between the moment of the UPDATE\nrequest and the original GET.\n\nThis can be considered a so-called \"Compare And Swap\", or CAS\noperation.\n\nOther than that, the two endpoints are identical in behavior.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "a528b632-4101-46ff-9647-62031d8554af",
          "name": "putSnippetsUsernameEncodedNode",
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
            "method": "PUT",
            "body": {
              "mode": "raw"
            },
            "description": "Identical to `UPDATE /snippets/encoded_id`, except that this endpoint\ntakes an explicit commit revision"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "f0fac373-99da-42f7-822d-bd2fe14431fc"
            }
          ]
        }
      ]
    }
  ]
}