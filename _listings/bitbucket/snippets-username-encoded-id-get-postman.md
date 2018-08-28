{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded",
    "_postman_id": "fb2a03c8-f388-4e9c-85bf-043a58980169",
    "description": "Retrieves a single snippet.\n\nSnippets support multiple content types:\n\n* application/json\n* multipart/related\n* multipart/form-data\n\n\napplication/json\n----------------\n\nThe default content type of the response is `application/json`.\nSince JSON is always `utf-8`, it cannot reliably contain file contents\nfor files that are not text. Therefore, JSON snippet documents only\ncontain the filename and links to the file contents.\n\nThis means that in order to retrieve all parts of a snippet, N+1\nrequests need to be made (where N is the number of files in the\nsnippet).\n\n\nmultipart/related\n-----------------\n\nTo retrieve an entire snippet in a single response, use the\n`Accept: multipart/related` HTTP request header.\n\n    $ curl -H \"Accept: multipart/related\" https://api.bitbucket.org/2.0/snippets/evzijst/1\n\nResponse:\n\n    HTTP/1.1 200 OK\n    Content-Length: 2214\n    Content-Type: multipart/related; start=\"snippet\"; boundary=\"===============1438169132528273974==\"\n    MIME-Version: 1.0\n\n    --===============1438169132528273974==\n    Content-Type: application/json; charset=\"utf-8\"\n    MIME-Version: 1.0\n    Content-ID: snippet\n\n    {\n      \"links\": {\n        \"self\": {\n          \"href\": \"https://api.bitbucket.org/2.0/snippets/evzijst/kypj\"\n        },\n        \"html\": {\n          \"href\": \"https://bitbucket.org/snippets/evzijst/kypj\"\n        },\n        \"comments\": {\n          \"href\": \"https://api.bitbucket.org/2.0/snippets/evzijst/kypj/comments\"\n        },\n        \"watchers\": {\n          \"href\": \"https://api.bitbucket.org/2.0/snippets/evzijst/kypj/watchers\"\n        },\n        \"commits\": {\n          \"href\": \"https://api.bitbucket.org/2.0/snippets/evzijst/kypj/commits\"\n        }\n      },\n      \"id\": kypj,\n      \"title\": \"My snippet\",\n      \"created_on\": \"2014-12-29T22:22:04.790331+00:00\",\n      \"updated_on\": \"2014-12-29T22:22:04.790331+00:00\",\n      \"is_private\": false,\n      \"files\": {\n        \"foo.txt\": {\n          \"links\": {\n            \"self\": {\n              \"href\": \"https://api.bitbucket.org/2.0/snippets/evzijst/kypj/files/367ab19/foo.txt\"\n            },\n            \"html\": {\n              \"href\": \"https://bitbucket.org/snippets/evzijst/kypj#file-foo.txt\"\n            }\n          }\n        },\n        \"image.png\": {\n          \"links\": {\n            \"self\": {\n              \"href\": \"https://api.bitbucket.org/2.0/snippets/evzijst/kypj/files/367ab19/image.png\"\n            },\n            \"html\": {\n              \"href\": \"https://bitbucket.org/snippets/evzijst/kypj#file-image.png\"\n            }\n          }\n        }\n      ],\n      \"owner\": {\n        \"username\": \"evzijst\",\n        \"display_name\": \"Erik van Zijst\",\n        \"uuid\": \"{d301aafa-d676-4ee0-88be-962be7417567}\",\n        \"links\": {\n          \"self\": {\n            \"href\": \"https://api.bitbucket.org/2.0/users/evzijst\"\n          },\n          \"html\": {\n            \"href\": \"https://bitbucket.org/evzijst\"\n          },\n          \"avatar\": {\n            \"href\": \"https://bitbucket-staging-assetroot.s3.amazonaws.com/c/photos/2013/Jul/31/erik-avatar-725122544-0_avatar.png\"\n          }\n        }\n      },\n      \"creator\": {\n        \"username\": \"evzijst\",\n        \"display_name\": \"Erik van Zijst\",\n        \"uuid\": \"{d301aafa-d676-4ee0-88be-962be7417567}\",\n        \"links\": {\n          \"self\": {\n            \"href\": \"https://api.bitbucket.org/2.0/users/evzijst\"\n          },\n          \"html\": {\n            \"href\": \"https://bitbucket.org/evzijst\"\n          },\n          \"avatar\": {\n            \"href\": \"https://bitbucket-staging-assetroot.s3.amazonaws.com/c/photos/2013/Jul/31/erik-avatar-725122544-0_avatar.png\"\n          }\n        }\n      }\n    }\n\n    --===============1438169132528273974==\n    Content-Type: text/plain; charset=\"us-ascii\"\n    MIME-Version: 1.0\n    Content-Transfer-Encoding: 7bit\n    Content-ID: \"foo.txt\"\n    Content-Disposition: attachment; filename=\"foo.txt\"\n\n    foo\n\n    --===============1438169132528273974==\n    Content-Type: image/png\n    MIME-Version: 1.0\n    Content-Transfer-Encoding: base64\n    Content-ID: \"image.png\"\n    Content-Disposition: attachment; filename=\"image.png\"\n\n    iVBORw0KGgoAAAANSUhEUgAAABQAAAAoCAYAAAD+MdrbAAABD0lEQVR4Ae3VMUoDQRTG8ccUaW2m\n    TKONFxArJYJamCvkCnZTaa+VnQdJSBFl2SMsLFrEWNjZBZs0JgiL/+KrhhVmJRbCLPx4O+/DT2TB\n    cbblJxf+UWFVVRNsEGAtgvJxnLm2H+A5RQ93uIl+3632PZyl/skjfOn9Gvdwmlcw5aPUwimG+NT5\n    EnNN036IaZePUuIcK533NVfal7/5yjWeot2z9ta1cAczHEf7I+3J0ws9Cgx0fsOFpmlfwKcWPuBQ\n    73Oc4FHzBaZ8llq4q1mr5B2mOUCt815qYR8eB1hG2VJ7j35q4RofaH7IG+Xrf/PfJhfmwtfFYoIN\n    AqxFUD6OMxcvkO+UfKfkOyXfKdsv/AYCHMLVkHAFWgAAAABJRU5ErkJggg==\n    --===============1438169132528273974==--\n\nmultipart/form-data\n-------------------\n\nAs with creating new snippets, `multipart/form-data` can be used as an\nalternative to `multipart/related`. However, the inherently flat\nstructure of form-data means that only basic, root-level properties\ncan be returned, while nested elements like `links` are omitted:\n\n    $ curl -H \"Accept: multipart/form-data\" https://api.bitbucket.org/2.0/snippets/evzijst/kypj\n\nResponse:\n\n    HTTP/1.1 200 OK\n    Content-Length: 951\n    Content-Type: multipart/form-data; boundary=----------------------------63a4b224c59f\n\n    ------------------------------63a4b224c59f\n    Content-Disposition: form-data; name=\"title\"\n    Content-Type: text/plain; charset=\"utf-8\"\n\n    My snippet\n    ------------------------------63a4b224c59f--\n    Content-Disposition: attachment; name=\"file\"; filename=\"foo.txt\"\n    Content-Type: text/plain\n\n    foo\n\n    ------------------------------63a4b224c59f\n    Content-Disposition: attachment; name=\"file\"; filename=\"image.png\"\n    Content-Transfer-Encoding: base64\n    Content-Type: application/octet-stream\n\n    iVBORw0KGgoAAAANSUhEUgAAABQAAAAoCAYAAAD+MdrbAAABD0lEQVR4Ae3VMUoDQRTG8ccUaW2m\n    TKONFxArJYJamCvkCnZTaa+VnQdJSBFl2SMsLFrEWNjZBZs0JgiL/+KrhhVmJRbCLPx4O+/DT2TB\n    cbblJxf+UWFVVRNsEGAtgvJxnLm2H+A5RQ93uIl+3632PZyl/skjfOn9Gvdwmlcw5aPUwimG+NT5\n    EnNN036IaZePUuIcK533NVfal7/5yjWeot2z9ta1cAczHEf7I+3J0ws9Cgx0fsOFpmlfwKcWPuBQ\n    73Oc4FHzBaZ8llq4q1mr5B2mOUCt815qYR8eB1hG2VJ7j35q4RofaH7IG+Xrf/PfJhfmwtfFYoIN\n    AqxFUD6OMxcvkO+UfKfkOyXfKdsv/AYCHMLVkHAFWgAAAABJRU5ErkJggg==\n    ------------------------------5957323a6b76--",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "74d0e4d8-9069-4946-a288-779715c015f6",
          "name": "getSnippetsUsernameEncoded",
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
            "method": "GET",
            "body": {
              "mode": "raw"
            },
            "description": "Retrieves a single snippet"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "ce9cb424-f18e-4008-8bc1-865043ade4db"
            }
          ]
        }
      ]
    }
  ]
}