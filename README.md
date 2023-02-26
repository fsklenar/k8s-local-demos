# k8s-local-demos
Demos for Kubernetes local installation

# Notes

### Ingress installation

https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-helm/

#### Adding the Helm Repository

This step is required if you’re installing the chart via the helm repository.

<code>$ helm repo add nginx-stable https://helm.nginx.com/stable
$ helm repo update</code>

#### Installing via Helm Repository

To install the chart with the release name my-release (my-release is the name that you choose):

For NGINX:

<code>$ helm install ingress-nginx nginx-stable/nginx-ingress -n nginx-ingress --create-namespace</code>


### Static LAN IP
By default ingress is not visible in your LAN, only internally from master/worker nodes.
First you have to set Static IP for ingress  

 - choose one IP from your LAN CIDR (example 192.168.0.220)
 - add this IP to master or worker node (netplan in Ubuntu)

Edit nginx-ingress service

    kubectl edit service nginx-ingress-nginx-ingress

 add

    spec:
     externalIPs:
     - <any_local_IP>

### Edit Ingress external traffic policy

    kubectl edit service nginx-ingress-nginx-ingress
change:

    externalTrafficPolicy: Cluster


