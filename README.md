# Minimal reproduction

[Github issue](https://github.com/renovatebot/renovate/issues/14551)
[Logs](https://github.com/renovatebot/renovate/issues/14551)

## Current behavior

Renovate fails to create a PR when using

```
// renovate.json
{
  "groupName": "all deps",
  "matchPaths": ["+(package.json)"]
}
```

together with these deps

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

## Expected behavior

Should be able to create a PR containing all these three deps
