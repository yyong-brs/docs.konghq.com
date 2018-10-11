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

### Bar Docs

Bar and bar and links to Foo
