# k8snovice15
Kubernetes Novice Tokyo #15 demo

https://k8s-novice-jp.connpass.com/event/229951/

```shell
CLUSTER_NAME=k8snovice
CLUSTER_REGION=ap-northeast-1
```

```shell
eksctl create cluster --name $CLUSTER_NAME --region $CLUSTER_REGION --fargate
```

<details><summary>output...</summary>

```console
2021-12-04 08:07:13 [ℹ]  eksctl version 0.76.0
2021-12-04 08:07:13 [ℹ]  using region ap-northeast-1
2021-12-04 08:07:13 [ℹ]  setting availability zones to [ap-northeast-1c ap-northeast-1a ap-northeast-1d]
2021-12-04 08:07:13 [ℹ]  subnets for ap-northeast-1c - public:192.168.0.0/19 private:192.168.96.0/19
2021-12-04 08:07:13 [ℹ]  subnets for ap-northeast-1a - public:192.168.32.0/19 private:192.168.128.0/19
2021-12-04 08:07:13 [ℹ]  subnets for ap-northeast-1d - public:192.168.64.0/19 private:192.168.160.0/19
2021-12-04 08:07:13 [ℹ]  using Kubernetes version 1.21
2021-12-04 08:07:13 [ℹ]  creating EKS cluster "k8snovice" in "ap-northeast-1" region with Fargate profile
2021-12-04 08:07:13 [ℹ]  if you encounter any issues, check CloudFormation console or try 'eksctl utils describe-stacks --region=ap-northeast-1 --cluster=k8snovice'
2021-12-04 08:07:13 [ℹ]  CloudWatch logging will not be enabled for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 08:07:13 [ℹ]  you can enable it with 'eksctl utils update-cluster-logging --enable-types={SPECIFY-YOUR-LOG-TYPES-HERE (e.g. all)} --region=ap-northeast-1 --cluster=k8snovice'
2021-12-04 08:07:13 [ℹ]  Kubernetes API endpoint access will use default of {publicAccess=true, privateAccess=false} for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 08:07:13 [ℹ]
2 sequential tasks: { create cluster control plane "k8snovice",
    2 sequential sub-tasks: {
        wait for control plane to become ready,
        create fargate profiles,
    }
}
2021-12-04 08:07:13 [ℹ]  building cluster stack "eksctl-k8snovice-cluster"
2021-12-04 08:07:13 [ℹ]  deploying stack "eksctl-k8snovice-cluster"
2021-12-04 08:07:43 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:08:13 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:09:13 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:10:13 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:11:13 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:12:13 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:13:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:14:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:15:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:16:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:17:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:18:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:19:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:20:14 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 08:22:15 [ℹ]  creating Fargate profile "fp-default" on EKS cluster "k8snovice"
2021-12-04 08:26:34 [ℹ]  created Fargate profile "fp-default" on EKS cluster "k8snovice"
2021-12-04 08:29:04 [ℹ]  "coredns" is now schedulable onto Fargate
2021-12-04 08:30:07 [ℹ]  "coredns" is now scheduled onto Fargate
2021-12-04 08:30:07 [ℹ]  "coredns" pods are now scheduled onto Fargate
2021-12-04 08:30:07 [ℹ]  waiting for the control plane availability...
2021-12-04 08:30:07 [✔]  saved kubeconfig as "/home/cloudshell-user/.kube/config"
2021-12-04 08:30:07 [ℹ]  no tasks
2021-12-04 08:30:07 [✔]  all EKS cluster resources for "k8snovice" have been created
2021-12-04 08:30:07 [✖]  kubectl not found, v1.10.0 or newer is required
2021-12-04 08:30:07 [ℹ]  cluster should be functional despite missing (or misconfigured) client binaries
2021-12-04 08:30:07 [✔]  EKS cluster "k8snovice" in "ap-northeast-1" region is ready
```
</details>

```shell
eksctl utils associate-iam-oidc-provider --cluster=$CLUSTER_NAME --region=$CLUSTER_REGION
```
```console
2021-12-04 08:49:53 [ℹ]  eksctl version 0.76.0
2021-12-04 08:49:53 [ℹ]  using region ap-northeast-1
2021-12-04 08:49:53 [ℹ]  (plan) would create IAM Open ID Connect provider for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 08:49:53 [!]  no changes were applied, run again with '--approve' to apply the changes
```
```shell
eksctl utils associate-iam-oidc-provider --cluster=$CLUSTER_NAME --region=$CLUSTER_REGION --approve
```
```console
2021-12-04 08:50:12 [ℹ]  eksctl version 0.76.0
2021-12-04 08:50:12 [ℹ]  using region ap-northeast-1
2021-12-04 08:50:13 [ℹ]  will create IAM Open ID Connect provider for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 08:50:13 [✔]  created IAM Open ID Connect provider for cluster "k8snovice" in "ap-northeast-1"
```

```shell
eksctl create fargateprofile --cluster $CLUSTER_NAME --name fp-demo --namespace demo
```
```console
2021-12-04 09:35:28 [ℹ]  eksctl version 0.76.0
2021-12-04 09:35:28 [ℹ]  using region ap-northeast-1
2021-12-04 09:35:29 [ℹ]  creating Fargate profile "fp-demo" on EKS cluster "k8snovice"
2021-12-04 09:37:39 [ℹ]  created Fargate profile "fp-demo" on EKS cluster "k8snovice"
```

```shell
kubectl create ns demo

eksctl create iamserviceaccount \
  --cluster=$CLUSTER_NAME \
  --namespace=demo \
  --name=demo-sa \
  --attach-policy-arn=arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess \
  --override-existing-serviceaccounts \
  --region $CLUSTER_REGION \
  --approve
```
```console
2021-12-04 08:52:20 [ℹ]  eksctl version 0.76.0
2021-12-04 08:52:20 [ℹ]  using region ap-northeast-1
2021-12-04 08:52:21 [ℹ]  1 iamserviceaccount (demo/demo-sa) was included (based on the include/exclude rules)
2021-12-04 08:52:21 [!]  metadata of serviceaccounts that exist in Kubernetes will be updated, as --override-existing-serviceaccounts was set
2021-12-04 08:52:21 [ℹ]  1 task: {
    2 sequential sub-tasks: {
        create IAM role for serviceaccount "demo/demo-sa",
        create serviceaccount "demo/demo-sa",
    } }2021-12-04 08:52:21 [ℹ]  building iamserviceaccount stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 08:52:21 [ℹ]  deploying stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 08:52:21 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 08:52:37 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 08:52:54 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 08:52:54 [ℹ]  created serviceaccount "demo/demo-sa"
```

```shell
kubectl -n demo get sa demo-sa -o yaml
```
```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  annotations:
    eks.amazonaws.com/role-arn: arn:aws:iam::XXXXXXXXXXXX:role/eksctl-k8snovice-addon-iamserviceaccount-dem-Role1-I25W8IGOXPBL
  creationTimestamp: "2021-12-04T08:52:54Z"
  labels:
    app.kubernetes.io/managed-by: eksctl
  name: demo-sa
  namespace: demo
  resourceVersion: "6249"
  uid: 7fea5c44-c3a5-4e4d-b801-1f5fcfd10bc3
secrets:
- name: demo-sa-token-pqxs9
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    eks.amazonaws.com/fargate-profile: fp-demo
  name: irsa
  namespace: demo
spec:
  containers:
  - args:
    - s3
    - ls
    image: amazon/aws-cli
    name: aws
  restartPolicy: Never
  serviceAccountName: demo-sa
  tolerations:
  - key: "eks.amazonaws.com/compute-type"
    operator: "Equal"
    value: "fargate"
    effect: "NoSchedule"
```
