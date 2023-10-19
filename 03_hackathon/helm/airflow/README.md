# Airflow on kubernetes

This readme is to install airflow on a local kubernetes cluster and enable gitsync to let airflow sync the dags to you airflow cluster.

Install `helm` with `brew install helm`.

Fill in your github private key in the `./git-sync-secret.yaml` file and then apply this.
```
kubectl create ns airflow
kubectl apply -n airflow -f git-sync-secret.yaml
```

Install airflow with the specific `values.yaml`.
```
helm upgrade --install airflow apache-airflow/airflow --namespace airflow --create-namespace -f ./values.yaml
```

Wait till all the pods in `airflow` are in `running` state and then do the port-forward to excess your webui:
```bash
kubectl port-forward svc/airflow-webserver 8080:8080 --namespace airflow
```