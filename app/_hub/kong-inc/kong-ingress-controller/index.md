---

name: Kong Ingress Controller
publisher: Kong Inc.
version: 0.2.x

desc: Ingress controller for Kubernetes that utilizes Kong as a reverse proxy and load balancer
description: |
  Ingress controller for Kubernetes that utilizes Kong as a reverse proxy and load balancer.

enterprise: false
type: integration
categories:
  - traffic-control

kong_version_compatibility:
    community_edition:
      compatible:
        - 0.14.x
      incompatible:
        - 0.13.x
    enterprise_edition:
      incompatible:
        - 0.32-x
        - 0.33-x

---

### Docs go here

Using a standard Kubernetes deployment, the Ingress controller runs multiple containers in a single pod. This allows us to define in a unit containing an initContainer to run Kong migrations, one container for the Kong admin API in control-plane mode and one container for the ingress controller itself. With this approach we simplify the deploy of the required components without user intervention. Once the deployment passes the readiness and liveness probes it means the Kong migrations ran and ingress controller can communicate with the Kong admin API.

and so on...
