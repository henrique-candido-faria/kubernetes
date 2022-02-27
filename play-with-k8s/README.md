# PLAY WITH KUBERNETES

## Initializes cluster master node ##
  kubeadm config images pull
  kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16

## Initialize cluster networking ##
  kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml

## Alternatively, if you are the root user, you can run:
  export KUBECONFIG=/etc/kubernetes/admin.conf

## You should now deploy a pod network to the cluster.
## Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at: https://kubernetes.io/docs/concepts/cluster-administration/addons/
  kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"

## Then you can join any number of worker nodes by running the following on each as root:
  kubeadm join 192.168.0.22:6443 --token 1ggylb.clpmppzg0rdbs3yt \
    --discovery-token-ca-cert-hash sha256:2e14b65e4ab6c06b4a5411a6fca9ddd7e5cae30f942f4dddc8bbac96e0945a48
