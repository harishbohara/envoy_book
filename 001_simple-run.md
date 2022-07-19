### Run envoy with updated config
Normally envoy run on port 10000 but we have chnaged to it to run on '9902'

```
envoy -c 001_simple-run.yaml
```

Use ```--log-path``` to redirect log to a file
```
 envoy -c 001_simple-run.yaml --log-path logs/custom.log
```

See the envoy config on ```http://localhost:9902/```

#### Validate your yaml file
You can check your file before you run
```
envoy --mode validate -c 001_simple-run.yaml
```