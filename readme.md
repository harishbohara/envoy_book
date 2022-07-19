
This project has some samples to understand Envoy proxy. You can go to <file>.md files to learn. 

### Some helper commands
Get the admin UI - if configured
```
http://localhost:9902/
```

---
### A working sample
```
brew install envoy 
envoy -c 003_first_listener.yaml --log-path logs/custom.log
```

Try the "003_first_listener.yaml" -> it works and http://localhost:10000 loads "https://www.envoyproxy.io/"

---
### Building your own control plane

Get the sample control plane
```
>> git clone https://github.com/envoyproxy/go-control-plane.git

>> make example
This will run envoy and also runs the sample
```

If you already have your own envoy running, just run following - this is a control plane which is doing the job of ```003_first_listener.yaml``` via code:
  - this example sets a listeeer at port 10000
  - setup a route "/" to call cluster
  - setup a cluster which will loads "https://www.envoyproxy.io/"
```
go run internal/example/main/main.go --debug=true
```
