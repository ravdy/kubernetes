Liveness probes and readiness probes are Kubernetes mechanisms that help ensure your applications are running smoothly and are available to serve traffic. Here's a brief explanation of each:

### **Liveness Probe**

A liveness probe checks if an application inside a pod is running. If the liveness probe fails, Kubernetes will kill the pod and restart it. This is useful for detecting and remedying situations where an application might be stuck or deadlocked.

### **Readiness Probe**

A readiness probe checks if an application inside a pod is ready to serve traffic. If the readiness probe fails, Kubernetes will remove the pod from the pool of service endpoints until it passes. This ensures that only healthy pods receive traffic.

let's start with the Kubernetes deployment file for an Apache HTTP Server, including readiness and liveness probes:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: apache-server
spec:
  replicas: 1
  selector:
    matchLabels:
      app: apache-server
  template:
    metadata:
      labels:
        app: apache-server
    spec:
      containers:
      - name: apache-server
        image: httpd:2.4
        ports:
        - name: http
          containerPort: 80
        livenessProbe:
          httpGet:
            path: /
            port: 80
          initialDelaySeconds: 15
          periodSeconds: 20
        readinessProbe:
          httpGet:
            path: /
            port: 80
          initialDelaySeconds: 5
          periodSeconds: 10

```

Save this content to a file, say `apache-deployment.yaml`, and then apply it using the command: `kubectl apply -f apache-deployment.yaml`.

Next, here's an example of a Kubernetes service file for the Apache HTTP Server deployment:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: apache-service
spec:
  type: NodePort
  ports:
  - port: 80
    targetPort: 80
    protocol: TCP
    name: http
    nodePort: 30080  # You can specify a port number within the range 30000-32767 or leave it for Kubernetes to allocate automatically.
  selector:
    app: apache-server

```

In this file, a Service of type `LoadBalancer` is created, exposing the Apache server on port 80. The `targetPort` is the port on the Pods that the Service forwards incoming connections to. The `selector` field is used to select the Pods that the Service should route traffic to.

Save this content to a file, say `apache-service.yaml`, and then apply it using the command: `kubectl apply -f apache-service.yaml`.
