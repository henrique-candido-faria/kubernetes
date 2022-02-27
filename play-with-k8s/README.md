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
  kubeadm join 192.168.0.13:6443 --token 92q4cf.e8he2nb5zr7iwjua \
    --discovery-token-ca-cert-hash sha256:37f6da71053d02c12a0cd16dd0d0ee4f78b1ab33f5149893bf0160a6a353a2f3
