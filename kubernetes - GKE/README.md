# nginx-app — Kubernetes Image Test Project

A minimal Kubernetes setup to deploy and test a cleanstart nginx Docker image (`cleanstart/nginx:latest-dev`).

---

## Project Structure

```
nginx-app/
├── namespace.yaml       # Namespace: nginx-app
├── deployment.yaml      # Deployment with liveness probe
├── service.yaml         # LoadBalancer Service on port 80
└── README.md
```

---

## Prerequisites

- `kubectl` configured and pointing to your cluster
- Docker image `cleanstart/nginx:latest-dev` pushed to a registry accessible by your cluster

---

## Deploy

Apply the manifests in order:

```bash
kubectl apply -f namespace.yaml
kubectl apply -f deployment.yaml -n nginx-app
kubectl apply -f service.yaml -n nginx-app
```

Or apply everything at once:

```bash
kubectl apply -f . -n nginx-app
```

---

## Verify

**Check pods are running:**
```bash
kubectl get pods -n nginx-app
```

**Check the service:**
```bash
kubectl get svc -n nginx-app
```

### kind cluster (local)

`LoadBalancer` services don't get an external IP in kind. Use port-forward instead:
```bash
kubectl port-forward svc/nginx-app-service 8080:80 -n nginx-app
```

Then in a separate terminal:
```bash
curl http://localhost:8080/  # Without index.html in this minimal image we dont see nginx home page
```

> Keep the port-forward terminal open while testing.

### Cloud cluster (for prod)

Wait for the external IP to be assigned (status changes from `<pending>` to an IP):
```bash
kubectl get svc -n nginx-app -w
```

Then test:
```bash
curl http://<EXTERNAL-IP>/
```

---

## Test Image Functionality

First, get your pod name — you'll need it for the steps below:
```bash
kubectl get pods -n nginx-app
```

> For kind, replace `<HOST>` with `localhost:8080` (port-forward must be running).
> For cloud, replace `<HOST>` with the external IP from `kubectl get svc -n nginx-app`.

---

### 1. HTTP Response & Status Codes

Check the root endpoint returns a `200 OK`:
```bash
curl -v http://<HOST>/
```

Check only the status code of any path:
```bash
curl -o /dev/null -s -w "%{http_code}\n" http://<HOST>/
```

Test a non-existent path to verify your custom 404 handling:
```bash
curl -o /dev/null -s -w "%{http_code}\n" http://<HOST>/does-not-exist
```

Check response headers (server version, custom headers, etc.):
```bash
curl -I http://<HOST>/
```

---

### 2. Logs & Container Behavior

Stream live logs — run this first, then send requests in another terminal to see them logged in real time:
```bash
kubectl logs -f <POD-NAME> -n nginx-app
```

Check logs from the previous container instance (useful after a crash or restart):
```bash
kubectl logs <POD-NAME> -n nginx-app --previous
```

Inspect pod events and restart count:
```bash
kubectl describe pod <POD-NAME> -n nginx-app
```

---

## Teardown

```bash
kubectl delete namespace nginx-app
```

This removes the namespace along with all resources inside it.