# Kubernetes Novice Tokyo #15 demo

https://k8s-novice-jp.connpass.com/event/229951/

## IAM Roles for Service Accounts （AWS）

EKSクラスターを作成する。

```shell
CLUSTER_NAME=k8snovice
CLUSTER_REGION=ap-northeast-1
```

```shell
eksctl create cluster --name $CLUSTER_NAME --region $CLUSTER_REGION --fargate
```

<details><summary>output...</summary>

```console
2021-12-04 10:05:44 [ℹ]  eksctl version 0.76.0
2021-12-04 10:05:44 [ℹ]  using region ap-northeast-1
2021-12-04 10:05:44 [ℹ]  setting availability zones to [ap-northeast-1c ap-northeast-1d ap-northeast-1a]
2021-12-04 10:05:44 [ℹ]  subnets for ap-northeast-1c - public:192.168.0.0/19 private:192.168.96.0/19
2021-12-04 10:05:44 [ℹ]  subnets for ap-northeast-1d - public:192.168.32.0/19 private:192.168.128.0/19
2021-12-04 10:05:44 [ℹ]  subnets for ap-northeast-1a - public:192.168.64.0/19 private:192.168.160.0/19
2021-12-04 10:05:44 [ℹ]  using Kubernetes version 1.21
2021-12-04 10:05:44 [ℹ]  creating EKS cluster "k8snovice" in "ap-northeast-1" region with Fargate profile
2021-12-04 10:05:44 [ℹ]  if you encounter any issues, check CloudFormation console or try 'eksctl utils describe-stacks --region=ap-northeast-1 --cluster=k8snovice'
2021-12-04 10:05:44 [ℹ]  CloudWatch logging will not be enabled for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 10:05:44 [ℹ]  you can enable it with 'eksctl utils update-cluster-logging --enable-types={SPECIFY-YOUR-LOG-TYPES-HERE (e.g. all)} --region=ap-northeast-1 --cluster=k8snovice'
2021-12-04 10:05:44 [ℹ]  Kubernetes API endpoint access will use default of {publicAccess=true, privateAccess=false} for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 10:05:44 [ℹ]
2 sequential tasks: { create cluster control plane "k8snovice",
    2 sequential sub-tasks: {
        wait for control plane to become ready,
        create fargate profiles,
    }
}
2021-12-04 10:05:44 [ℹ]  building cluster stack "eksctl-k8snovice-cluster"
2021-12-04 10:05:45 [ℹ]  deploying stack "eksctl-k8snovice-cluster"
2021-12-04 10:06:15 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:06:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:07:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:08:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:09:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:10:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:11:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:12:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:13:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:14:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:15:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:16:45 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:17:46 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:18:46 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:19:46 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-cluster"
2021-12-04 10:21:46 [ℹ]  creating Fargate profile "fp-default" on EKS cluster "k8snovice"
2021-12-04 10:26:05 [ℹ]  created Fargate profile "fp-default" on EKS cluster "k8snovice"
2021-12-04 10:28:35 [ℹ]  "coredns" is now schedulable onto Fargate
2021-12-04 10:29:38 [ℹ]  "coredns" is now scheduled onto Fargate
2021-12-04 10:29:38 [ℹ]  "coredns" pods are now scheduled onto Fargate
2021-12-04 10:29:38 [ℹ]  waiting for the control plane availability...
2021-12-04 10:29:38 [✔]  saved kubeconfig as "/home/cloudshell-user/.kube/config"
2021-12-04 10:29:38 [ℹ]  no tasks
2021-12-04 10:29:38 [✔]  all EKS cluster resources for "k8snovice" have been created
2021-12-04 10:29:39 [ℹ]  kubectl command should work with "/home/cloudshell-user/.kube/config", try 'kubectl get nodes'
2021-12-04 10:29:39 [✔]  EKS cluster "k8snovice" in "ap-northeast-1" region is ready
```
</details>

IAM OIDCプロバイダーを作成する。

```shell
eksctl utils associate-iam-oidc-provider --cluster=$CLUSTER_NAME --region=$CLUSTER_REGION
```
```console
2021-12-04 10:32:59 [ℹ]  eksctl version 0.76.0
2021-12-04 10:32:59 [ℹ]  using region ap-northeast-1
2021-12-04 10:33:00 [ℹ]  (plan) would create IAM Open ID Connect provider for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 10:33:00 [!]  no changes were applied, run again with '--approve' to apply the changes
```
```shell
eksctl utils associate-iam-oidc-provider --cluster=$CLUSTER_NAME --region=$CLUSTER_REGION --approve
```
```console
2021-12-04 10:33:47 [ℹ]  eksctl version 0.76.0
2021-12-04 10:33:47 [ℹ]  using region ap-northeast-1
2021-12-04 10:33:48 [ℹ]  will create IAM Open ID Connect provider for cluster "k8snovice" in "ap-northeast-1"
2021-12-04 10:33:48 [✔]  created IAM Open ID Connect provider for cluster "k8snovice" in "ap-northeast-1"
```

Fargateプロファイルを作成する。`demo` NamespaceにPodを作成できるようにする。

```shell
eksctl create fargateprofile --cluster $CLUSTER_NAME --name fp-demo --namespace demo
```
```console
2021-12-04 10:34:53 [ℹ]  eksctl version 0.76.0
2021-12-04 10:34:53 [ℹ]  using region ap-northeast-1
2021-12-04 10:34:54 [ℹ]  creating Fargate profile "fp-demo" on EKS cluster "k8snovice"
2021-12-04 10:37:04 [ℹ]  created Fargate profile "fp-demo" on EKS cluster "k8snovice"
```

`demo` Namespaceを作成する。

```shell
kubectl create ns demo
```

AWS管理の`AmazonS3ReadOnlyAccess` IAMポリシーを割り当てるServiceAccountを作成する。

カスタマー管理のIAMポリシーを利用する場合は別途作成する。

```shell
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
2021-12-04 10:39:06 [ℹ]  eksctl version 0.76.0
2021-12-04 10:39:06 [ℹ]  using region ap-northeast-1
2021-12-04 10:39:07 [ℹ]  1 iamserviceaccount (demo/demo-sa) was included (based on the include/exclude rules)
2021-12-04 10:39:07 [!]  metadata of serviceaccounts that exist in Kubernetes will be updated, as --override-existing-serviceaccounts was set
2021-12-04 10:39:07 [ℹ]  1 task: {
    2 sequential sub-tasks: {
        create IAM role for serviceaccount "demo/demo-sa",
        create serviceaccount "demo/demo-sa",
    } }2021-12-04 10:39:07 [ℹ]  building iamserviceaccount stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 10:39:07 [ℹ]  deploying stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 10:39:07 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 10:39:23 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 10:39:40 [ℹ]  waiting for CloudFormation stack "eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa"
2021-12-04 10:39:40 [ℹ]  created serviceaccount "demo/demo-sa"
```

次のようなServiceAccountが作成される。

```shell
kubectl -n demo get sa demo-sa -o yaml
```
```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  annotations:
    eks.amazonaws.com/role-arn: arn:aws:iam::XXXXXXXXXXXX:role/eksctl-k8snovice-addon-iamserviceaccount-dem-Role1-1CG76ZJ14V5MC
  creationTimestamp: "2021-12-04T10:39:40Z"
  labels:
    app.kubernetes.io/managed-by: eksctl
  name: demo-sa
  namespace: demo
  resourceVersion: "4220"
  uid: 7c7b0d81-37ca-4405-a296-cacf4905d1de
secrets:
- name: demo-sa-token-cv6cv
```

`aws s3 ls`を実行するPodを作成する。

```shell
kubectl apply -f irsa.yaml
```

実行終了まで待つ。Fargateを利用しているため、少々時間がかかる。

```shell
kubectl -n demo get po irsa -w
```
```console
NAME   READY   STATUS    RESTARTS   AGE
irsa   0/1     Pending   0          41s
irsa   0/1     Pending   0          55s
irsa   0/1     ContainerCreating   0          55s
irsa   1/1     Running             0          2m1s
irsa   0/1     Completed           0          3m19s
```

S3バケット一覧がログに出力されていることを確認する。

```shell
kubectl -n demo logs irsa
```
```console
2021-10-09 08:16:41 cf-templates-nbptwbxafkg5-ap-northeast-1
2021-05-03 08:55:29 cf-templates-nbptwbxafkg5-us-east-1
```

比較のため、ServiceAccountの指定のみ異なるPodを実行する。

```shell
kubectl apply -f no-irsa.yaml
```

先程同様、実行終了まで待ってからログを確認する。

```shell
kubectl -n demo get po no-irsa -w
```
```console
NAME      READY   STATUS              RESTARTS   AGE
no-irsa   0/1     ContainerCreating   0          61s
no-irsa   1/1     Running             0          2m
no-irsa   0/1     Error               0          3m16s
```

```shell
kubectl -n demo logs no-irsa
```
```console
Unable to locate credentials. You can configure credentials by running "aws configure".
```

めでたしめでたし。

利用しないリソースを削除する。

- CloudFormationの`eksctl-k8snovice-addon-iamserviceaccount-demo-demo-sa`スタック
- EKSクラスター

```shell
eksctl delete cluster --name $CLUSTER_NAME --region $CLUSTER_REGION
```
