{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Revision Diff",
    "_postman_id": "eaeb41ac-4eeb-4fdf-bda0-fe6da06ff35d",
    "description": "Returns the diff of the specified commit against its first parent.\n\nNote that this resource is different in functionality from the `patch`\nresource.\n\nThe differences between a diff and a patch are:\n\n* patches have a commit header with the username, message, etc\n* diffs support the optional `path=foo/bar.py` query param to filter the\n  diff to just that one file diff (not supported for patches)\n* for a merge, the diff will show the diff between the merge commit and\n  its first parent (identical to how PRs work), while patch returns a\n  response containing separate patches for each commit on the second\n  parent's ancestry, up to the oldest common ancestor (identical to\n  its reachability).\n\nNote that the character encoding of the contents of the diff is\nunspecified as Git and Mercurial do not track this, making it hard for\nBitbucket to reliably determine this.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "875a5abb-2c2d-42a1-a422-042f68c7e07d",
          "name": "getSnippetsUsernameEncodedRevisionDiff",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/:revision/diff"
              ],
              "query": [
                {
                  "key": "path",
                  "value": "%7B%7D",
                  "disabled": false
                }
              ],
              "variable": [
                {
                  "id": "encoded_id",
                  "value": "{}",
                  "type": "string"
                },
                {
                  "id": "revision",
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
            "description": "Returns the diff of the specified commit against its first parent"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "8946e1fa-e71a-4a86-a0fb-e55ed62c1cc1"
            }
          ]
        }
      ]
    }
  ]
}