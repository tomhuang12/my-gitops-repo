# Demonstrate tf-controller with localstack

Once localstack is running, port forward localstack
```bash
export POD_NAME=$(kubectl get pods --namespace localstack -l "app.kubernetes.io/name=localstack,app.kubernetes.io/instance=localstack" -o jsonpath="{.items[0].metadata.name}")
kubectl -n localstack port-forward $POD_NAME 8080:4566
```

When tf-runner finishes applying, list created S3 buckets
```bash
aws --endpoint-url=http://localhost:8080 s3api list-buckets
```
