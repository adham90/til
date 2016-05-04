## Enable gzip compression
The `ngx_http_gzip_module` module is a filter that compresses responses using the “gzip” method. This often helps to reduce the size of transmitted data by half or even more.

```nginx
#enable gzip
gzip on;

#disable gziping for IE6
gzip_disable "msie6";

#level of compression recommended 2..4
gzip_comp_level 3;

#what to compress
gzip_types text/plain;
gzip_types text/css;
gzip_types application/json;
gzip_types text/javascript;
```
