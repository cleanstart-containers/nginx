# CleanStart Nginx - Complete Production Deployment

A comprehensive, production-ready Kubernetes deployment for CleanStart Nginx web server. This single-file deployment includes all necessary components for a robust, scalable, and secure web server setup.

## 🚀 Overview

This deployment provides a complete Nginx solution on Kubernetes with:

- **Production-ready configuration** with security headers, compression, and performance optimizations
- **Multiple service types** (ClusterIP, NodePort, LoadBalancer) for different access patterns
- **Horizontal Pod Autoscaling** for automatic scaling based on CPU and memory usage
- **Pod Disruption Budget** for high availability during updates
- **Network Policies** for enhanced security
- **Comprehensive monitoring** with Prometheus metrics and health checks
- **Interactive web interface** for testing and validation

## Quick Start

### Pull Commands
```bash
docker pull ghcr.io/cleanstart-containers/nginx:latest
docker pull ghcr.io/cleanstart-containers/nginx:latest-dev
```

### Run Commands

Basic test:
```bash
docker run -it --name openldap-test ghcr.io/cleanstart-containers/nginx:latest-dev
```

## 📋 Prerequisites

- Kubernetes cluster (v1.19+)
- `kubectl` configured and connected to your cluster
- Access to CleanStart Nginx image (`ghcr.io/cleanstart-containers/nginx:latest`)
- Sufficient cluster resources (minimum 2 nodes recommended for HPA)

### Resource Requirements

- **CPU**: 100m request, 200m limit per pod
- **Memory**: 128Mi request, 256Mi limit per pod
- **Storage**: EmptyDir volumes for logs and cache
- **Network**: Port 80 for HTTP traffic

## 📄 License

This deployment is open source and available under the [MIT License](LICENSE).

## Resources

- **Official Documentation:** https://nginx.org/en/docs/
- **Provenance / SBOM / Signature:** https://images.cleanstart.com/images/nginx
- **Docker Hub:** https://hub.docker.com/r/cleanstart/nginx
- **CleanStart All Images:** https://images.cleanstart.com
- **CleanStart Community Images:** https://hub.docker.com/u/cleanstart

### Vulnerability Disclaimer

CleanStart offers Docker images that include third-party open-source libraries and packages maintained by independent contributors. While CleanStart maintains these images and applies industry-standard security practices, it cannot guarantee the security or integrity of upstream components beyond its control.

Users acknowledge and agree that open-source software may contain undiscovered vulnerabilities or introduce new risks through updates. CleanStart shall not be liable for security issues originating from third-party libraries, including but not limited to zero-day exploits, supply chain attacks, or contributor-introduced risks.

Security remains a shared responsibility: CleanStart provides updated images and guidance where possible, while users are responsible for evaluating deployments and implementing appropriate controls.
