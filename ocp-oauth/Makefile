#
#
#
deploy:
	oc new-app --template jupyterhub-ocp-oauth
	kubectl apply -f quickstart.yaml

undeploy:
	oc delete all,configmap,pvc,serviceaccount,rolebinding --selector app=jupyterhub
	kubectl delete -f quickstart.yaml

status:
	oc rollout status dc/jupyterhub

deploy-template:
	kustomize build . | kubectl apply -f -

undeploy-template:
	kustomize build . | kubectl delete -f -
