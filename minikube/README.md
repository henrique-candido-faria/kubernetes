# IINSTALAÇÃO
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube
cp minikube /usr/local/bin
rm minikube

# OPERAÇÃO
minikube version
minikube start
minikube status
minikube ssh
minikube ip
minikube stop
minikube dashboard
minikube delete
