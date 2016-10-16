## openresty-url-shortener

A server block that uses nginx + lua and the goo.gl API to generate short URLs.

Cached responses range from 20 to 80ms.  
Fresh responses range from 150 to 300ms.

##### Requires
- NGINX + ngx_http_lua_module
- lua-resty-http
- lua-cjson

These directives should be in the main nginx configuration:
```
lua_ssl_trusted_certificate /etc/nginx/cacert.pem; # https://curl.haxx.se/ca/cacert.pem
lua_ssl_verify_depth 3;
  
init_by_lua_block {
    cjson = require "cjson"
    http = require "resty.http"
}
```
