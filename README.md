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
docker tag supermarket-app:1.0.0 547223838688.dkr.ecr.eu-west-2.amazonaws.com/supermarket-app:1.0.0
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

