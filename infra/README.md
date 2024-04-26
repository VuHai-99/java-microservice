- Run local k8s
  - Run postgres db
    - `kubectl apply -f postgres-deployment.yml`
  - (Initial) Install Helm Charts
    - `helm install local-confluent-kafka helm/cp-helm-charts --version 0.6.0`
  - Run microservices
    - `kubectl apply -f application-deployment-local.yml`

- Stop local k8s
    - Run postgres db
        - `kubectl delete -f postgres-deployment.yml`
    - Install Helm Charts
        - `helm delete local-confluent-kafka`
    - Run microservices
        - `kubectl delete -f application-deployment-local.yml`

- Get k8s pods info:
  - `kubectl get pods`