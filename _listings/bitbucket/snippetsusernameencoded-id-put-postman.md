{
  "info": {
    "name": "Bitbucket Update Snippets Username Encoded",
    "_postman_id": "6214c7af-3713-4a68-9ec7-4c036d3c6d47",
    "description": "Used to update a snippet. Use this to add and delete files and to\nchange a snippet's title.\n\nTo update a snippet, one can either PUT a full snapshot, or only the\nparts that need to be changed.\n\nThe contract for PUT on this API is that properties missing from the\nrequest remain untouched so that snippets can be efficiently\nmanipulated with differential payloads.\n\nTo delete a property (e.g. the title, or a file), include its name in\nthe request, but omit its value (use `null`).\n\nAs in Git, explicit renaming of files is not supported. Instead, to\nrename a file, delete it and add it again under another name. This can\nbe done atomically in a single request. Rename detection is left to\nthe SCM.\n\nPUT supports three different content types for both request and\nresponse bodies:\n\n* `application/json`\n* `multipart/related`\n* `multipart/form-data`\n\nThe content type used for the request body can be different than that\nused for the response. Content types are specified using standard HTTP\nheaders.\n\nUse the `Content-Type` and `Accept` headers to select the desired\nrequest and response format.\n\n\napplication/json\n----------------\n\nAs with creation and retrieval, the content type determines what\nproperties can be manipulated. `application/json` does not support\nfile contents and is therefore limited to a snippet's meta data.\n\nTo update the title, without changing any of its files:\n\n    $ curl -X POST -H \"Content-Type: application/json\" https://api.bitbucket.org/2.0/snippets/evzijst/kypj             -d '{\"title\": \"Updated title\"}'\n\n\nTo delete the title:\n\n    $ curl -X POST -H \"Content-Type: application/json\" https://api.bitbucket.org/2.0/snippets/evzijst/kypj             -d '{\"title\": null}'\n\nNot all parts of a snippet can be manipulated. The owner and creator\nfor instance are immutable.\n\n\nmultipart/related\n-----------------\n\n`multipart/related` can be used to manipulate all of a snippet's\nproperties. The body is identical to a POST. properties omitted from\nthe request are left unchanged. Since the `start` part contains JSON,\nthe mechanism for manipulating the snippet's meta data is identical\nto `application/json` requests.\n\nTo update one of a snippet's file contents, while also changing its\ntitle:\n\n    PUT /2.0/snippets/evzijst/kypj HTTP/1.1\n    Content-Length: 288\n    Content-Type: multipart/related; start=\"snippet\"; boundary=\"===============1438169132528273974==\"\n    MIME-Version: 1.0\n\n    --===============1438169132528273974==\n    Content-Type: application/json; charset=\"utf-8\"\n    MIME-Version: 1.0\n    Content-ID: snippet\n\n    {\n      \"title\": \"My updated snippet\",\n      \"files\": {\n          \"foo.txt\": {}\n        }\n    }\n\n    --===============1438169132528273974==\n    Content-Type: text/plain; charset=\"us-ascii\"\n    MIME-Version: 1.0\n    Content-Transfer-Encoding: 7bit\n    Content-ID: \"foo.txt\"\n    Content-Disposition: attachment; filename=\"foo.txt\"\n\n    Updated file contents.\n\n    --===============1438169132528273974==--\n\nHere only the parts that are changed are included in the body. The\nother files remain untouched.\n\nNote the use of the `files` list in the JSON part. This list contains\nthe files that are being manipulated. This list should have\ncorresponding multiparts in the request that contain the new contents\nof these files.\n\nIf a filename in the `files` list does not have a corresponding part,\nit will be deleted from the snippet, as shown below:\n\n    PUT /2.0/snippets/evzijst/kypj HTTP/1.1\n    Content-Length: 188\n    Content-Type: multipart/related; start=\"snippet\"; boundary=\"===============1438169132528273974==\"\n    MIME-Version: 1.0\n\n    --===============1438169132528273974==\n    Content-Type: application/json; charset=\"utf-8\"\n    MIME-Version: 1.0\n    Content-ID: snippet\n\n    {\n      \"files\": {\n        \"image.png\": {}\n      }\n    }\n\n    --===============1438169132528273974==--\n\nTo simulate a rename, delete a file and add the same file under\nanother name:\n\n    PUT /2.0/snippets/evzijst/kypj HTTP/1.1\n    Content-Length: 212\n    Content-Type: multipart/related; start=\"snippet\"; boundary=\"===============1438169132528273974==\"\n    MIME-Version: 1.0\n\n    --===============1438169132528273974==\n    Content-Type: application/json; charset=\"utf-8\"\n    MIME-Version: 1.0\n    Content-ID: snippet\n\n    {\n        \"files\": {\n          \"foo.txt\": {},\n          \"bar.txt\": {}\n        }\n    }\n\n    --===============1438169132528273974==\n    Content-Type: text/plain; charset=\"us-ascii\"\n    MIME-Version: 1.0\n    Content-Transfer-Encoding: 7bit\n    Content-ID: \"bar.txt\"\n    Content-Disposition: attachment; filename=\"bar.txt\"\n\n    foo\n\n    --===============1438169132528273974==--\n\n\nmultipart/form-data\n-----------------\n\nAgain, one can also use `multipart/form-data` to manipulate file\ncontents and meta data atomically.\n\n    $ curl -X PUT http://localhost:12345/2.0/snippets/evzijst/kypj             -F title=\"My updated snippet\" -F file=@foo.txt\n\n    PUT /2.0/snippets/evzijst/kypj HTTP/1.1\n    Content-Length: 351\n    Content-Type: multipart/form-data; boundary=----------------------------63a4b224c59f\n\n    ------------------------------63a4b224c59f\n    Content-Disposition: form-data; name=\"file\"; filename=\"foo.txt\"\n    Content-Type: text/plain\n\n    foo\n\n    ------------------------------63a4b224c59f\n    Content-Disposition: form-data; name=\"title\"\n\n    My updated snippet\n    ------------------------------63a4b224c59f\n\nTo delete a file, omit its contents while including its name in the\n`files` field:\n\n    $ curl -X PUT https://api.bitbucket.org/2.0/snippets/evzijst/kypj -F files=image.png\n\n    PUT /2.0/snippets/evzijst/kypj HTTP/1.1\n    Content-Length: 149\n    Content-Type: multipart/form-data; boundary=----------------------------ef8871065a86\n\n    ------------------------------ef8871065a86\n    Content-Disposition: form-data; name=\"files\"\n\n    image.png\n    ------------------------------ef8871065a86--\n\nThe explicit use of the `files` element in `multipart/related` and\n`multipart/form-data` is only required when deleting files.\nThe default mode of operation is for file parts to be processed,\nregardless of whether or not they are listed in `files`, as a\nconvenience to the client.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "486bb20e-2459-4724-9c3f-e0304cd53e6c",
          "name": "putSnippetsUsernameEncoded",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id"
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
            "method": "PUT",
            "body": {
              "mode": "raw"
            },
            "description": "Used to update a snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "546c57ad-2b64-47e9-a9db-f3c7f5fdf870"
            }
          ]
        }
      ]
    }
  ]
}