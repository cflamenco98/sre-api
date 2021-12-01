https://cert-manager.io/docs/installation/kubernetes/

helm repo add jetstack https://charts.jetstack.io
helm repo update

helm upgrade --install \
 cert-manager jetstack/cert-manager \
 --namespace cert-manager \
 --create-namespace \
 --version v1.3.0 \
 --set installCRDs=true \
 --set 'extraArgs={--dns01-recursive-nameservers-only,--dns01-recursive-nameservers=8.8.8.8:53\,1.1.1.1:53}'
