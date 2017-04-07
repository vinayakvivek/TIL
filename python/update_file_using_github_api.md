# Update file using Github API
> 08/04/2017, scilab-on-cloud

There is a python package [PyGithub](https://github.com/PyGithub/PyGithub) which lets you use github APIs easily.
But as of now, there is a bug in the implementation of `update_file()` function.

So I had to do in the hard way; using `requests`.

The corresponding API endpoint is [this](https://developer.github.com/v3/repos/contents/#update-a-file)

Since updating a file requires permissions, you need to get an [ACCESS_TOKEN](https://github.com/settings/tokens) with permission to edit repos.
