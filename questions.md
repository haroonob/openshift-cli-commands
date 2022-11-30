# Q1# Nodejs code fix and deploy app

`oc new-app --name greet --build-env npm_config_registry=http://${RHT_OCP4_NEXUS_SERVER}/repository/nodejs nodejs:12~https://github.com/${RHT_OCP4_GITHUB_USER}/DO288-apps#source-build --context-dir nodejs-helloworld`

`oc start-build --follow bc/greet`


# Q2# Optimize and Build Container and deploy app 

`podman build --layers=false -t do288-hello-java ./hello-java --format=docker`

`podman tag do288-hello-java quay.io/${RHT_OCP4_QUAY_USER}/do288-hello-java`

`podman login quay.io -u ${RHT_OCP4_QUAY_USER}`

`podman push --format v2s1  quay.io/${RHT_OCP4_QUAY_USER}/do288-hello-java`

`oc new-app  --name elvis quay.io/${RHT_OCP4_QUAY_USER}/do288-hello-java`

# Q3# import image and config map

`oc new-project ${RHT_OCP4_DEV_USER}-common`

`oc create secret generic quayio --from-file .dockerconfigjson=${XDG_RUNTIME_DIR}/containers/auth.json  --type kubernetes.io/dockerconfigjson`

`oc secretes link default nameofsecret --for=pull `

`oc import-image php-info --confirm --reference-policy local --from quay.io/${RHT_OCP4_QUAY_USER}/php-info`


`oc create configmap configmapname --from-literal key=value`

`oc set env deployment/application --from configmap/properties`


# Q4# source to image 
`changes in .s2i file.` 

`cp -Rf /tmp/src/*.html ./`

`DATE=date "+%b %d, %Y @ %H:%M %p"`

`echo "---> Creating info page"`
`echo "Page built on $DATE" >> ./info.html`
`echo "Proudly served by Apache HTTP Server version $HTTPD_VERSION" >> ./info.html`

# Q#6 build hook
`oc rsh quotesapi-7d76ff58f8-6j2gx `
Pwd
`oc set build-hook bc/app --post-commit --script="python /opt/app-root/src/abc.py"`
`oc start-build bc/app -F`

# Q#7 live probes 
oc set probe deployment probes --liveness --get-url=http://:8080/healthz --initial-delay-seconds=2 --timeout-seconds=2

oc set probe deployment probes --readiness --get-url=http://:8080/ready --initial-delay-seconds=2 --timeout-seconds=2
# Q8# internal registery
oc patch config.imageregistry cluster -n openshift-image-regisrty --type merge -p '{"spec":{"defaultRoute":true}}'
oc get route -n openshift-image-registry

TOKEN=$(oc whoami -t)

# Q#9 templates


# Q10# helm chart 
`helm install famousapp .`


