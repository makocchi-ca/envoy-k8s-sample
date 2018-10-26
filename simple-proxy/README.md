# run

```bash
$ kubectl apply -f simple-proxy/
```

This sample uses `default` namespace.  
If you want to change namespace, please create namespace.

```bash
$ kubectl create namespace simple-proxy
$ kubectl apply -n simple-proxy simple-proxy/
```

# check

Please set your `<front-envoy-endpoint>` as you like. (ex. `kubectl expose`)  
Default service type is `ClusterIP`.

```bash
$ curl http://<front-envoy-endpoint>/service/1
service1-764bc49fdb-4pp6p

$ curl http://<front-envoy-endpoint>/service/2
service2-66668c767c-prt7t
```

# cleanup

```bash
$ kubectl delete -f simple-proxy/

# or kubectl delete namespace simple-proxy
```
