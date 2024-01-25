

# k8s-local-demos
Demos for Kubernetes local installation

## DEMO01
- NGINX deployment + Service + Ingress

### Ingress installation INGRESS-NGINX

https://kubernetes.github.io/ingress-nginx/deploy/

### Static LAN IP
By default ingress is not visible in your LAN, only internally from master/worker nodes.
First you have to set Static IP for ingress  

 - choose one IP from your LAN CIDR (example 192.168.0.220)
 - add this IP to master or worker node (netplan in Ubuntu)

### Prepare values.yaml for ingress-nginx

 - fill-in your LAN IP into ingress-nginx/values.yaml

#### *Installing via Helm Repository*

To install the chart with the release name ingress-nginx:

For NGINX:

    export INGRESS_NGINX_VER=4.9.0
    helm upgrade ingress-nginx --version ${INGRESS_NGINX_VER} -i -f ingress-nginx/values.yaml --namespace ingress-nginx --create-namespace ingress-nginx/ingress-nginx




