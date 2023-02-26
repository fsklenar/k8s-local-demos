# k8s-local-demos
Demos for Kubernetes local installation

# Notes

### Ingress installation

TBD

### Static LAN IP
By default ingress is not visible in your LAN, only internally from master/worker nodes.
First you have to set Static IP for ingress  

 - choose one from your LAN CIDR
 - add this IP to master or worker node

Edit nginx-ingress service

    kubectl edit service nginx-ingress-nginx-ingress

 Add

    spec:
     externalIPs:
     - 192.168.0.230

### Edit Ingress external traffic policy

    kubectl edit service nginx-ingress-nginx-ingress
change:

    externalTrafficPolicy: Cluster


