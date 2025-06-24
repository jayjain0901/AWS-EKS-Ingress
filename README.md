# AWS-EKS-Ingress

    1  aws configure
    2  ls
    3  eksctl create cluster --name demo-cluster --region us-east-1 --fargate
    4  aws eks update-kubeconfig --name demo-cluster --region us-east-1
    5  eksctl create fargateprofile     --cluster demo-cluster     --region us-east-1     --name alb-sample-app     --namespace game-2048
    6  kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/examples/2048/2048_full.yaml
    7  kubectl get pods -n game-2048
    8  kubectl get pods -n game-2048 -w
    9  kubectl get svc -n game-2048 
   10  kubectl get ingress -n game-2049
   11  kubectl get ingress -n game-2048
   12  eksctl utils associate-iam-oidc-provider --cluster demo-cluster  --approve
   13  eksctl utils associate-iam-oidc-provider --cluster demo-cluster  --approve
   14  eksctl utils associate-iam-oidc-provider --region us-east-1 --cluster demo-cluster --approve
   15  curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.11.0/docs/install/iam_policy.json
   16  aws iam create-policy     --policy-name AWSLoadBalancerControllerIAMPolicy     --policy-document file://iam_policy.json
   17  eksctl create iamserviceaccount   --cluster=<your-cluster-name>   --namespace=kube-system   --name=aws-load-balancer-controller   --role-name AmazonEKSLoadBalancerControllerRole   --attach-policy-arn=arn:aws:iam::<your-aws-account-id>:policy/AWSLoadBalancerControllerIAMPolicy   --approve
   18  eksctl create iamserviceaccount   --cluster=demo-cluster   --namespace=kube-system   --name=aws-load-balancer-controller   --role-name AmazonEKSLoadBalancerControllerRole   --attach-policy-arn=arn:aws:iam::039612881980:policy/AWSLoadBalancerControllerIAMPolicy   --approve
   19  eksctl create iamserviceaccount   --cluster=demo-cluster --region=us-east-1  --namespace=kube-system   --name=aws-load-balancer-controller   --role-name AmazonEKSLoadBalancerControllerRole   --attach-policy-arn=arn:aws:iam::039612881980:policy/AWSLoadBalancerControllerIAMPolicy   --approve
   20  helm repo add eks https://aws.github.io/eks-charts
   21  helm repo update eks
   22  helm install aws-load-balancer-controller eks/aws-load-balancer-controller \            
   23    -n kube-system   --set clusterName=demo-cluster   --set serviceAccount.create=false   --set serviceAccount.name=aws-load-balancer-controller   --set region=us-east-1   --set vpcId=vpc-0c385ac0aa876fb49
   24  helm install aws-load-balancer-controller eks/aws-load-balancer-controller   -n kube-system   --set clusterName=demo-cluster   --set serviceAccount.create=false   --set serviceAccount.name=aws-load-balancer-controller   --set region=us-east-1   --set vpcId=vpc-0c385ac0aa876fb49
   25  kubectl get deployment -n kube-system aws-load-balancer-controller
   26  kubectl get deployment -n kube-system aws-load-balancer-controller -w
   27  kubectl get ingress -n game-2048
   28  history
   29  history > my_commands.txt
