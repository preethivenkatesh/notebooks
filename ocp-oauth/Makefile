#
#
#
generate:
	oc new-app --template jupyterhub-ocp-oauth -oyaml > all.yaml && \
	./process all.yaml items

ungenerate:
	rm -f kustomization.yaml *-*.yaml all.yaml

deploy:
	kustomize build . | kubectl apply -f -

undeploy:
	oc delete all,configmap,pvc,serviceaccount,rolebinding --selector app=jupyterhub

status:
	oc rollout status dc/jupyterhub
