Authentication:
    openssl genrsa -out akash.key 2048
    openssl req -new -key akash.key -out akash.csr -subj "/CN=akash/O=tw"
    openssl x509 -req -in akash.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out akash.crt -days 1
    kubectl config view
    kubectl --kubeconfig akash.kubeconfig config set-cluster akash-kubernetes --server https://142.93.218.166:6443 --certificate-authority=ca.crt
    kubectl --kubeconfig akash.kubeconfig config set-credentials akash --client-certificate akash.crt --client-key akash.key
    kubectl --kubeconfig akash.kubeconfig config set-context akash-context --cluster akash-kubernetes --namespace akash --user akash

Authorization:
    kubectl create role akash-admin-role --verb=get,list --resource=pods --namespace akash
    kubectl create rolebinding akash-admin-role-binding --role=akash-admin-role --user=akash --namespace akash


    https://github.deere.com/ECommerce/ecommerce-prod-api/tree/gh-pages/build-reports/6077c176308c8126a1b476fca63d1e8c0c3e09a4/2215040/1/tests/test
    https://github.deere.com/pages/ECommerce/ecommerce-prod-api/build-reports/6077c176308c8126a1b476fca63d1e8c0c3e09a4/2215040/1/tests/test/index.html



    https://github.deere.com/pages/ECommerce/ecommerce-prodex-bff/build-reports/4b35243e8c04f6ee2f8a9b3b82a5f10629e90d85/2201903/1/tests/test/index.html

    https://github.deere.com/pages/ECommerce/ecommerce-prodex-bff/build-reports/4b35243e8c04f6ee2f8a9b3b82a5f10629e90d85/2201903/1/tests/integrationTest/index.html