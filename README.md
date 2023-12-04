# supermarket-app

## Build Docker Image

```
sudo docker build -t supermarket-app:1.0.0 .
```

Login to ECR

```
aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin 547223838688.dkr.ecr.eu-west-2.amazonaws.com
```


Tag the image

```
docker tag supermarket-app:1.0.0 547223838688.dkr.ecr.us-west-2.amazonaws.com/supermarket-app:1.0.0
```
Push to ECR

```
docker push 547223838688.dkr.ecr.eu-west-2.amazonaws.com/supermarket-app:1.0.0
```


## EKS Provisioning

Create Cluster

```
eksctl create cluster -f eks-cluster.yaml
```

Update Kubeconfig

```
aws eks update-kubeconfig --region us-west-2 --name eks-supermarket-cluster
```

## Cluster Security

1. Setup RBAC - IAM integration for different permission levels
2. Setup external secrets operater for secrets handling (AWS secrets managers)
3. Implement Network Policy.
4. Run CIS benchmarks for Compliance Auditing
5. Implement TLS for ELB/ingress endpoints
6. Implement IAC for cluster provisioning.
7. Scan IAC code using policy as code tools like checkov to ensure cluster tags and best practices are following.


## Container Security

1. Implement linting (Hadolint)
2. Implement Contianer Vulnerability scanning (Trivy)
3. Use distroless minimal base images.