# Firebase hosting header rules

## TL;DR

The last matching rule in the array is the one that is going to be applied.

## Details

When trying to setup Firebase Hosting rules I've found out that the order in which the rules are in the array matters.

Dummy folder structure that's being served via a Google Cloud Run Container:

```
_nuxt/123.js
_nuxt/123.css
```

```json
{
  "hosting": {
    "public": "hosting",
    "trailingSlash": true,
    "rewrites": [
      {
        "source": "/graphql",
        "function": "app"
      },
      {
        "source": "**",
        "run": { "serviceId": "your-nuxt-server", "region": "us-central1" }
      }
    ],
    "headers": [
      {
        "source": "**",
        "headers": [{ "key" : "Cache-Control", "value" : "no-store" }]
      },
      {
        "source": "/static-pages-from-cms/**",
        "headers": [{ "key" : "Cache-Control", "value" : "max-age=300, public" }]
      },
      {
        "source": "/",
        "headers": [{ "key" : "Cache-Control", "value" : "max-age=300, public" }]
      },
      {
        "source" : "**/*.@(js|css)",
        "headers" : [
          { "key" : "Cache-Control", "value" : "max-age=29030400, public" },
          { "key": "Access-Control-Allow-Origin", "value": "*" }
        ]
      },
      {
        "source" : "**/*.@(jpg|jpeg|gif|png|svg|woff2|mp3)",
        "headers" : [
          { "key" : "Cache-Control", "value" : "max-age=29030400, public" },
          { "key": "Access-Control-Allow-Origin", "value": "*" }
        ]
      },
      {
        "source" : "**/*.@(html)",
        "headers" : [
          { "key" : "Cache-Control", "value" : "max-age=29030400, public" },
          { "key": "Access-Control-Allow-Origin", "value": "*" }
        ]
      }
    ]
  }
}
```

See the headers rule `**` is at the top. If it was on the bottom it would overwrite all rules above and no request would be cached.

Note: Requests to cached urls will be served from Firebase Hosting directly and they will not ping the docker container on every request.
