# run

```bash
$ kubectl apply -f simple-with-jaeger/
```

This sample uses `default` namespace.  
If you want to change namespace, please create namespace.

```bash
$ kubectl create namespace simple-with-jaeger
$ kubectl apply -n simple-with-jaeger simple-with-jaeger/
```

# trace

Please set your `<front-envoy-endpoint>` as you like. (ex. `kubectl expose`)  
Default service type is `ClusterIP`.

### front-envoy -> service1

```bash
$ curl http://<front-envoy-endpoint>/
```

### front-envoy -> service1 -> service2

```bash
$ curl http://<front-envoy-endpoint>/trace/hoge
```

# Jaeger

Please check tracing results at jaeger GUI.  
Default jaeger service type is `NodePort`.

```bash
$ kubectl get service jaeger
NAME          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                          AGE
jaeger        NodePort    10.104.93.238   <none>        9411:31428/TCP,16686:31065/TCP   55s

# Jaeger ui port is 16686.
# Check http://<node ip>:31065/ at your browser.
```

# cleanup

```bash
$ kubectl delete -f simple-with-jaeger/

# or kubectl delete -n simple-with-jaeger -f simple-with-jaeger/
```
