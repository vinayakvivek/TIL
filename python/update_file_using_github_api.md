# Update file using Github API
> 08/04/2017, scilab-on-cloud

There is a python package [PyGithub](https://github.com/PyGithub/PyGithub) which lets you use github APIs easily.
But as of now, there is a bug in the implementation of `update_file()` function.

So I had to do in the hard way; using `requests`.

The corresponding API endpoint is [this](https://developer.github.com/v3/repos/contents/#update-a-file)

Since updating a file requires permissions, you need to get an [ACCESS_TOKEN](https://github.com/settings/tokens) with permission to edit repos.

Then we need to send a `PUT` request to the github API server.

The request must contain the following header fields
* Authorization
* Content-Type

It must also containt data as a json object.

```python
import requests
import base64
import json

headers = {
	'Authorization': 'token %s' % GITHUB_TOKEN,
	'Content-Type': 'application/json'
},
  
data = {
	"message" : "<commit_message>",
	"content": "<base64_encoded_content>",
	"sha": "<sha_of_file>",
}

url = 'https://api.github.com/repos/<username>/<repo_name>/contents/<path_to_file>
r = requests.put(url, headers=headers, data=json.dumps(data))
```

Thats it!

PS : `SHA` of the file can be obtained by a similar GET request OR you can use PyGithub
