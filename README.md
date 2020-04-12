# gitops-workshop


# Install flagger

helm repo add flagger https://flagger.app

kubectl apply -f https://raw.githubusercontent.com/weaveworks/flagger/master/artifacts/flagger/crd.yaml

helm upgrade -i flagger-loadtester flagger/loadtester --namespace prod

