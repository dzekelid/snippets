{
  "info": {
    "name": "Bitbucket Get Snippets Username Encoded  Revision Patch",
    "_postman_id": "d56e1468-dfaf-40e0-9b47-b88dfe3304bf",
    "description": "Returns the patch of the specified commit against its first\nparent.\n\nNote that this resource is different in functionality from the `diff`\nresource.\n\nThe differences between a diff and a patch are:\n\n* patches have a commit header with the username, message, etc\n* diffs support the optional `path=foo/bar.py` query param to filter the\n  diff to just that one file diff (not supported for patches)\n* for a merge, the diff will show the diff between the merge commit and\n  its first parent (identical to how PRs work), while patch returns a\n  response containing separate patches for each commit on the second\n  parent's ancestry, up to the oldest common ancestor (identical to\n  its reachability).\n\nNote that the character encoding of the contents of the patch is\nunspecified as Git and Mercurial do not track this, making it hard for\nBitbucket to reliably determine this.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "snippets",
      "item": [
        {
          "id": "7bfb6396-0236-4839-8840-0e5132be22b2",
          "name": "getSnippetsUsernameEncodedRevisionPatch",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.bitbucket.org",
              "path": [
                "2.0",
                "snippets/:username/:encoded_id/:revision/patch"
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
            "description": "Returns the patch of the specified commit against its first\nparent"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "50593a7f-bde7-4573-8a88-fbb1aa423e35"
            }
          ]
        }
      ]
    }
  ]
}