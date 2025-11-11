# CP-Flink GKE Example

## Install CFK Operator

1. Create a namespace for CFK
```bash
kubectl create namespace confluent
```

2. Install the CFK Operator
```bash
helm repo add confluentinc https://packages.confluent.io/helm
helm repo update
helm install confluent-operator confluentinc/cp-helm-charts
```

3. Verify the operator is running
```bash
kubectl get pods -n confluent
```

4. Follow instructions in [CFK Deployment with Next Gen Control Center](cfk/README.md)

## Install Flink

1. Install Cert Manager
```bash
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.12.0/cert-manager.yaml
```

2. Install CP Flink Operator
```bash
helm upgrade --install cp-flink-kubernetes-operator --version "~1.120.0" \
  confluentinc/flink-kubernetes-operator \
  --set watchNamespaces="{confluent}"
```

3. Install CMF 
```bash
helm upgrade --install cmf --version "~2.1.0" confluentinc/confluent-manager-for-apache-flink --namespace confluent --set cmf.sql.production=false
```

4. Verify the operator is running
```bash
kubectl get pods -n confluent
```

5. Follow instructions in [CMF Deployment](cmf/README.md) to complete the installation and setup your first Flink Application
