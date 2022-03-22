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

ogether with these deps in package.json

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

here is part of the logs. For more logs check [Logs](https://github.com/christoferolaison/renovate-body-is-too-long/blob/main/logs)

```
DEBUG: 422 Error thrown from GitHub(branch="renovate/all-deps")
{
  "err": {
    "name": "HTTPError",
    "code": "ERR_NON_2XX_3XX_RESPONSE",
    "timings": {
      "start": 1647950218440,
      "socket": 1647950218441,
      "lookup": 1647950218441,
      "connect": 1647950218451,
      "secureConnect": 1647950218464,
      "upload": 1647950218465,
      "response": 1647950218918,
      "end": 1647950218919,
      "phases": {
        "wait": 1,
        "dns": 0,
        "tcp": 10,
        "tls": 13,
        "request": 1,
        "firstByte": 453,
        "download": 1,
        "total": 479
      }
    },
    "message": "Response code 422 (Unprocessable Entity)",
    "stack": "HTTPError: Response code 422 (Unprocessable Entity)\n    at Request.<anonymous> (/home/ubuntu/renovateapp/node_modules/got/dist/source/as-promise/index.js:117:42)\n    at runMicrotasks (<anonymous>)\n    at processTicksAndRejections (internal/process/task_queues.js:95:5)",
    "options": {
      "headers": {
        "user-agent": "Renovate Bot (GitHub App 2740)",
        "accept": "application/vnd.github.machine-man-preview+json",
        "authorization": "***********",
        "content-type": "application/json",
        "content-length": "68855",
        "accept-encoding": "gzip, deflate, br"
      },
      "url": "https://api.github.com/repos/christoferolaison/renovate-body-is-too-long/pulls",
      "hostType": "github",
      "username": "",
      "password": "",
      "method": "POST",
      "http2": false
    },
    "response": {
      "statusCode": 422,
      "statusMessage": "Unprocessable Entity",
      "body": {
        "message": "Validation Failed",
        "errors": [
          {
            "resource": "Issue",
            "code": "custom",
            "field": "body",
            "message": "body is too long (maximum is 65536 characters)"
          }
        ],
        "documentation_url": "https://docs.github.com/rest/reference/pulls#create-a-pull-request"
      },
      "headers": {
        "server": "GitHub.com",
        "date": "Tue, 22 Mar 2022 11:56:58 GMT",
        "content-type": "application/json; charset=utf-8",
        "content-length": "242",
        "x-github-media-type": "github.v3; param=machine-man-preview; format=json",
        "x-ratelimit-limit": "5000",
        "x-ratelimit-remaining": "4958",
        "x-ratelimit-reset": "1647953347",
        "x-ratelimit-used": "42",
        "x-ratelimit-resource": "core",
        "access-control-expose-headers": "ETag, Link, Location, Retry-After, X-GitHub-OTP, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Used, X-RateLimit-Resource, X-RateLimit-Reset, X-OAuth-Scopes, X-Accepted-OAuth-Scopes, X-Poll-Interval, X-GitHub-Media-Type, X-GitHub-SSO, X-GitHub-Request-Id, Deprecation, Sunset",
        "access-control-allow-origin": "*",
        "strict-transport-security": "max-age=31536000; includeSubdomains; preload",
        "x-frame-options": "deny",
        "x-content-type-options": "nosniff",
        "x-xss-protection": "0",
        "referrer-policy": "origin-when-cross-origin, strict-origin-when-cross-origin",
        "content-security-policy": "default-src 'none'",
        "vary": "Accept-Encoding, Accept, X-Requested-With",
        "x-github-request-id": "817C:61C3:17231D9:18DADAE:6239B98A",
        "connection": "close"
      },
      "httpVersion": "1.1"
    }
  }
}
```



## Expected behavior

Should be able to create a PR containing all these 3 deps
