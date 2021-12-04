# k8snovice15
Kubernetes Novice Tokyo #15 demo

https://k8s-novice-jp.connpass.com/event/229951/

```shell
eksctl create cluster --name k8snovice --region ap-northeast-1 --fargate
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
