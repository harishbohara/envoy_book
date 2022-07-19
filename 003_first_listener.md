#### Command to run this:
```
envoy -c 003_first_listener.yaml --log-path logs/custom.log
```

### What is a listener?

You can think a listener as a server socket running ata a port you have asked for.

```
static_resources:
  listeners:
  - name: listener_0
    address:
      socket_address:
        address: 0.0.0.0
        port_value: 10000
```

Here we are saying to open a server socket at port 10000. It is just saying a server socket is listning on port 10000. Below we will see how things will work.

### Filter chain - http_connection_manager

Now we want to do listen for HTTP connections at port 10000. We have created a server socket i.e. listener at port 10000. Now we have to tell Envoy to do the job.
You will see we created a full filter chain and configured it to call "service_envoyproxy_io" cluster

### Cluster
It is the actual service which we want to call. In this example we cteated "service_envoyproxy_io" and pointed it to ```www.envoyproxy.io```