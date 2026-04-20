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

## Documentation Resources
Essential links and resources for further information
 
**CleanStart Images**: https://images.cleanstart.com/
 
**Community Images**:<br>
**Docker Hub**: https://hub.docker.com/u/cleanstart<br>
**GitHub**: https://github.com/cleanstart-containers<br>
**AWS ECR Public Gallery**: https://gallery.ecr.aws/cleanstart/
 
**Presence on Social Media**:<br>
**Community**: https://www.linkedin.com/groups/18324021/<br>
**YouTube**: https://www.youtube.com/@CleanStartOfficial<br>
 
**Contribute to Container Use Cases**: https://github.com/cleanstart-dev/cleanstart-use-cases/
