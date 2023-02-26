# k8s-local-demos
Demos for Kubernetes local installation

## DEMO01
- NGINX deployment + Service + Ingress

# Notes

### Ingress installation

https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-helm/

#### *Adding the Helm Repository*

This step is required if you’re installing the chart via the helm repository.

    helm repo add nginx-stable https://helm.nginx.com/stable
    helm repo update

#### *Installing via Helm Repository*

To install the chart with the release name my-release (my-release is the name that you choose):

For NGINX:

    helm install nginx-ingress nginx-stable/nginx-ingress -n nginx-ingress --create-namespace


### Static LAN IP
By default ingress is not visible in your LAN, only internally from master/worker nodes.
First you have to set Static IP for ingress  

 - choose one IP from your LAN CIDR (example 192.168.0.220)
 - add this IP to master or worker node (netplan in Ubuntu)

Edit nginx-ingress service

    kubectl edit service nginx-ingress-nginx-ingress -n nginx-ingress

 add

    spec:
     externalIPs:
     - <any_local_IP>

### Ingress external traffic policy
Change Ingress external traffic policy from `Local` to `Cluster`

    kubectl edit service nginx-ingress-nginx-ingress -n nginx-ingress
change:

    externalTrafficPolicy: Cluster


