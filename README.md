<img width="933" alt="image" src="https://user-images.githubusercontent.com/6023146/159495916-56e11206-29c2-41a5-a184-ff7e61ac28dd.png">


# Minimal reproduction

[Github issue](https://github.com/renovatebot/renovate/issues/14551)

[Logs](https://github.com/christoferolaison/renovate-body-is-too-long/blob/main/logs)

## Current behavior

Renovate fails to create a PR when using the following rules: 

```
// renovate.json
{
  "groupName": "all deps",
  "matchPaths": ["+(package.json)"]
}
```

Together with these deps in package.json

```
// package.json
{
  "dependencies": {
    "esbuild": "0.11.6",
    "i18next": "20.4.0",
    "json-schema-faker": "0.5.0-rcv.41"
  }
}
```
For more details please take a look at the [logs](https://github.com/christoferolaison/renovate-body-is-too-long/blob/main/logs)




## Expected behavior

Should be able to create a PR containing an upgrade of all these 3 deps
