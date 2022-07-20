### How a external control plane like istio works
Istio uses xDS APIs and calls Envoy to setup listeners. We have created a serup where Envoy will listen to this and a sample service will register a service

#### How to run
```
go run main/main.go --debug=true --port 18000 --nodeID test-id1

Run curl on other terminal:
 >> curl -v http://localhost:10007
    You should get 301 -> not launc this on browser
```

You should see following logs
```
022/07/20 14:39:12 nodeID "test-id1" requested type.googleapis.com/envoy.config.cluster.v3.Cluster[] and known map[]. Diff []
2022/07/20 14:39:12 respond type.googleapis.com/envoy.config.cluster.v3.Cluster[] version "" with version "1"
2022/07/20 14:39:12 nodeID "test-id1" requested type.googleapis.com/envoy.config.listener.v3.Listener[] and known map[]. Diff []
2022/07/20 14:39:12 respond type.googleapis.com/envoy.config.listener.v3.Listener[] version "" with version "1"
2022/07/20 14:39:12 nodeID "test-id1" requested type.googleapis.com/envoy.config.listener.v3.Listener[] and known map[]. Diff []
2022/07/20 14:39:12 open watch 1 for type.googleapis.com/envoy.config.listener.v3.Listener[] from nodeID "test-id1", version "1"
2022/07/20 14:39:12 nodeID "test-id1" requested type.googleapis.com/envoy.config.cluster.v3.Cluster[] and known map[]. Diff []
2022/07/20 14:39:12 open watch 2 for type.googleapis.com/envoy.config.cluster.v3.Cluster[] from nodeID "test-id1", version "1"
2022/07/20 14:39:12 stream 2 open for type.googleapis.com/envoy.config.route.v3.RouteConfiguration
2022/07/20 14:39:12 nodeID "test-id1" requested type.googleapis.com/envoy.config.route.v3.RouteConfiguration[local_route] and known map[]. Diff [local_route]
2022/07/20 14:39:12 respond type.googleapis.com/envoy.config.route.v3.RouteConfiguration[local_route] version "" with version "1"
2022/07/20 14:39:12 nodeID "test-id1" requested type.googleapis.com/envoy.config.route.v3.RouteConfiguration[local_route] and known map[local_route:{}]. Diff []
2022/07/20 14:39:12 open watch 3 for type.googleapis.com/envoy.config.route.v3.RouteConfiguration[local_route] from nodeID "test-id1", version "1"
```
