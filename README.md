Transitional Directives for OAuth2 Providers
===================
 
This repository is used to provide transitional support to OAuth2 providers who have not deployed an `oauth3.json` to the root of their user-facing sites.

Are you an OAuth2 Provider?
===================

You should add an OAuth3 directive directly to your website, not this repository.

For example, if users come to your site at `https://www.example.net` you should place your OAuth3 directive
at `https://example.net/oauth3.json`.

It's okay if `https://example.net/oauth3.json` redirects to `https://www.example.net/oauth3.json`.

It is **not okay** if `https://example.net/oauth3.json` redirects to `http://example.net/oauth3.json` (unsecured).

Add a Transitional Directive
==================

If the OAuth2 endpoints for your favorite site aren't listed here,
please create a [pull request](https://github.com/OAuth3/providers/new/master).

Directives should follow the format of [`example.com.json`](https://raw.githubusercontent.com/OAuth3/providers/master/example.com.json)

```json
{
  "authorization_dialog": {
    "method": "GET"
  , "url": "https://example-api.com/api/oauth3/authorization_dialog"
  }
, "access_token": {
    "method": "GET"
  , "url": "https://example-api.com/api/oauth3/access_token"
  , "params": {
      "redirect_uri": true
    }
  }
, "profile": {
    "method": "GET"
  , "url": "https://example-api.com/api/oauth3/accounts/:account_id"
  }
, "authn_scope": ""
}
```

Note that the name of the user-facing domain `example.com` is different from the API domain `example-api.com`.

Example: Facebook
-----------------

Note: user's interact with facebook at `https://www.facebook.com`, so we strip off the `https://` as well as the `www` to get `facebook.com.json`:

```json
{
  "authorization_dialog": {
    "method": "GET"
  , "url": "https://www.facebook.com/dialog/oauth"
  }
, "access_token": {
    "method": "GET"
  , "url": "https://graph.facebook.com/v2.5/oauth/access_token"
  , "params": {
      "redirect_uri": true
    }
  }
, "profile": {
    "method": "GET"
  , "url": "https://graph.facebook.com/v2.5/me"
  }
, "authn_scope": ""
}
```
