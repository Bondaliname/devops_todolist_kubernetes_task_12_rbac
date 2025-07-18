chmod +x bootstrap.sh
./bootstrap.sh

kubectl get pods

POD=$(kubectl get pod -l app=todoapp -o jsonpath="{.items[0].metadata.name}")
kubectl exec -it $POD -- sh

curl -s --cacert /var/run/secrets/kubernetes.io/serviceaccount/ca.crt \
     -H "Authorization: Bearer $(cat /var/run/secrets/kubernetes.io/serviceaccount/token)" \
     https://kubernetes.default.svc/api/v1/secrets
