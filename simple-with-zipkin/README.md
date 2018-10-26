# run

```bash
$ kubectl apply -f simple-with-zipkin/
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

# zipkin

Please check tracing results at zipkin GUI.  
Default zipkin service type is `NodePort`.

```bash
$ kubectl get service zipkin
NAME      TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
zipkin    NodePort   10.98.114.94   <none>        9411:32079/TCP   59s

# Check http://<node ip>:32079/ at your browser.
```
