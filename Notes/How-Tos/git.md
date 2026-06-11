
## Troubleshoot

test

### Connection Hung up
 
Is the connection is 'hung up' e.g. when pushing, try increasing the post buffer:

```bash
git config --global http.postBuffer 524288000
```

