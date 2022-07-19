### How to forward traffic
Suppose you want to call http://localhost:10000, and when this is called; you want to read from "www.envoyproxy.io" and retrun the result.

You will see the access logs:
```
[2022-07-19T20:03:23.642Z] "GET / HTTP/1.1" 200 - 0 3826 516 515 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36" "bbb0a9a9-dd90-45e3-8cbf-aeb48aed5ed9" "www.envoyproxy.io" "34.124.149.177:443"
```

### Disable access logs
Remove following
```
  access_log:
          - name: envoy.access_loggers.stdout
            typed_config:
              "@type": type.googleapis.com/envoy.extensions.access_loggers.stream.v3.StdoutAccessLog
```              