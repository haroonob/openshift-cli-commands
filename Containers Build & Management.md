##
`skopeo copy --format v2s1 oci:/home/student/DO288/labs/external-registry/ubi-sleep docker://quay.io/${RHT_OCP4_QUAY_USER}/ubi-sleep:1.0`

#
`TOKEN=$(oc whoami -t)`
`skopeo copy --format v2s1 --dest-creds=${RHT_OCP4_DEV_USER}:${TOKEN} oci:/home/student/DO288/labs/expose-registry/ubi-info docker://${INTERNAL_REGISTRY}/${RHT_OCP4_DEV_USER}-common/ubi-info:1.0`

# delete image 
`skopeo delete docker://registry url`
#
`podman search quay.io/ubi-sleep`

#
`podman build --format=docker --layers=false -t nameofimage . `
#
`podman build --format=docker --layers=false -t nameofimage .`
`podman run --name test -it rhscl/httpd-24-rhel7 bash` -- interactive mode
#
`podman run -d --name sleep quay.io/${RHT_OCP4_QUAY_USER}/ubi-sleep:1.0`
 `podman run --name test -u 1234 -p 8080:8080 -d s2i-sample-app`
#
`sudo docker run -d -t -i -e REDIS_NAMESPACE='staging' -e POSTGRES_ENV_POSTGRES_PASSWORD='foo' -e POSTGRES_ENV_POSTGRES_USER='bar' -e POSTGRES_ENV_DB_NAME='mysite_staging' -e POSTGRES_PORT_5432_TCP_ADDR='docker-db-1.hidden.us-east-1.rds.amazonaws.com' -e SITE_URL='staging.mysite.com' -p 80:80 --link redis:redis --name container_name dockerhub_id/image_name`



# following changes need to run container files to openshift 
## add LABEL 
    io.openshift.expose-services="8080:http"
    io.openshift.tags="apache, httpd
 change the port to 8080 or 
## Add a USER instruction for an unprivileged user
USER 1001

## Change the group ID and permissions of the folders 
RUN chgrp -R 0 /var/log/httpd /var/run/httpd && \
    chmod -R g=u /var/log/httpd /var/run/httpd