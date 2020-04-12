# gitops-workshop


# Install flagger

helm repo add flagger https://flagger.app

kubectl apply -f https://raw.githubusercontent.com/weaveworks/flagger/master/artifacts/flagger/crd.yaml

helm upgrade -i flagger-loadtester flagger/loadtester --namespace prod

helm upgrade -i flagger flagger/flagger --wait \
--namespace linkerd \
--set crd.create=false \
--set metricsServer=http://linkerd-prometheus:9090 \
--set meshProvider=linkerd


helm delete -i flagger-loadtester --namespace prod

helm upgrade -i flagger-loadtester flagger/flagger --wait \
--namespace linkerd \
--set crd.create=false \
--set metricsServer=http://linkerd-prometheus:9090 \
--set meshProvider=linkerd
