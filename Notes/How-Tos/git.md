
## Troubleshoot

test

### Connection Hung up
 
Is the connection is 'hung up' e.g. when pushing, try increasing the post buffer:

```bash
git config --global http.postBuffer 524288000
```

## Personal Access Token (with Obsidian)

In Github, under account, go to settings, then **Developer settings**. Then, under **Personal access tokens**, create a **Fine-grained token**. create a fine-grained access token for a given repository. Select the repository under the **Only select repositories** option, then add permissions for **Content**, and set it to **Read and Write**. To use the personal access token, use a URL like this:

```
https://<PERSONAL_ACCESS_TOKEN>@github.com/<USERNAME>/<REPO>.git
```

For example (obfuscated PAT):

```
https://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@github.com/ivarout/obsidian.git
```
