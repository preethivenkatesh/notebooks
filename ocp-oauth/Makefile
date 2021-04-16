#
#
#
generate:
	kubectl apply -f template.yaml && \
	oc new-app --template jupyterhub-ocp-oauth -oyaml > all.yaml && \
	./process all.yaml items

ungenerate:
	kubectl delete -f template.yaml && \
	rm -f kustomization.yaml *-*.yaml all.yaml

deploy:
	kustomize build . | kubectl apply -f -

undeploy:
	oc delete all,configmap,pvc,serviceaccount,rolebinding --selector app=jupyterhub

status:
	oc rollout status dc/jupyterhub
