#
#
#
generate:
	oc new-app --template jupyterhub-ocp-oauth -oyaml > all.yaml && \
	./process all.yaml items && \
	cat template.yaml | yq r - -P objects[1] | APPLICATION_NAME=jupyterhub NOTEBOOK_IMAGE=tensorflow-notebook envsubst > image-stream-tensorflow-notebook.yaml && \
  echo '- image-stream-tensorflow-notebook.yaml' >> kustomization.yaml

ungenerate:
	rm -f kustomization.yaml *-*.yaml all.yaml

deploy:
	kustomize build . | kubectl apply -f -

undeploy:
	oc delete all,configmap,pvc,serviceaccount,rolebinding --selector app=jupyterhub

status:
	oc rollout status dc/jupyterhub
