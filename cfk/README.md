# CFK Deployment with Next Gen Control Center

1. Create basic credentials for prometheus & alertmanager server
kubectl -n confluent create secret generic prometheus-credentials --from-file=basic.txt=./creds/prometheus-credentials-secret.txt
kubectl -n confluent create secret generic alertmanager-credentials --from-file=basic.txt=./creds/alertmanager-credentials-secret.txt

2. Create basic credentials for prometheus & alertmanager client
kubectl -n confluent create secret generic prometheus-client-creds --from-file=basic.txt=./creds/prometheus-client-credentials-secret.txt
kubectl -n confluent create secret generic alertmanager-client-creds --from-file=basic.txt=./creds/alertmanager-client-credentials-secret.txt

3. Order to apply the k8s yaml files:
    - kraft.yaml
    - kafka.yaml
    - sr.yaml
    - c3-ng.yaml
    