# park-health-assets

Compiled static assets for the **Park Health** app. Generated output — do not edit by hand.

Built from `projects/health-app/` in the private `parkvps-vault` repo and served by the
`park-health` Supabase edge function, which pins a commit SHA so each deploy serves one
consistent build.

Public only so the edge function can fetch it without a token. Contains no secrets: the
bundle carries the Supabase project URL and the publishable anon key, both of which are
sent to every browser by design and gated by row-level security. No health data here.

## Updating

```
npm run build            # in projects/health-app
cp -r web/dist/. <this repo>/
git commit -am "Rebuild assets" && git push
```

Then redeploy the edge function with `ASSET_REF` set to the new commit SHA.
