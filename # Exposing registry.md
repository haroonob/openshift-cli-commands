# Exposing registry 
https://access.redhat.com/documentation/en-us/openshift_container_platform/4.11/html/registry/securing-exposing-registry

`oc patch configs.imageregistry.operator.openshift.io/cluster --patch '{"spec":{"defaultRoute":true}}' --type=merge`
HOST=$(oc get route default-route -n openshift-image-registry --template='{{ .spec.host }}')

 `oc get secret -n openshift-ingress  router-certs-default -o go-template='{{index .data "tls.crt"}}' | base64 -d | sudo tee /etc/pki/ca-trust/source/anchors/${HOST}.crt  > /dev/nul`
 
 `oc patch configs.imageregistry.operator.openshift.io/cluster --patch '{"spec":{"defaultRoute":true}}' --type=merge`


 HOST=$(oc get route default-route -n openshift-image-registry --template='{{ .spec.host }}')

 podman login -u kubeadmin -p $(oc whoami -t) --tls-verify=false $HOST


 oc patch configs.imageregistry.operator.openshift.io/cluster --patch '{"spec":{"defaultRoute",true}}' --type=merge
 oc get route default-route -n openshift-image-registry --template={{.spec.host}}

  oc patch config.imageregistry cluster -n openshift-image-registry \
--type merge -p '{"spec":{"defaultRoute":true}}'

oc get route -n openshift-image-registry

TOKEN=$(oc whoami -t)

oc patch configs.imageregistry cluster -n openshift-image-registry --type merge --patch '{"spec":{"defaultRoute":true}}'