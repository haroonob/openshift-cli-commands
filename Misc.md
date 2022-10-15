# Start build 
`oc start-build --follow bc/greet`
`oc status`
`oc cancel-build name`
`oc delete bc/name`
`oc logs -f bc/name --tail 10` 

`oc set triggers bc/name --from-image=project/image:tag`
`oc set triggers bc/name --from-image=project/image:tag --remove`
`oc set triggers bc/name --from-gitlab`

# Create a new service account:
`oc create serviceaccount myserviceaccount`
# Modify the deployment configuration for the application
`oc patch dc/demo-app --patch '{"spec":{"template":{"spec":{"serviceAccountName": "myserviceaccount"}}}}'`
# Add the myserviceaccount service account to the anyuid SCC to run using a fixed userid in the container:
`oc adm policy add-scc-to-user anyuid -z myserviceaccount`

 # Allows a user to pull images from the internal registry in a given project.
`oc policy add-role-to-user system:image-puller user_name -n project_name`

# Grant service accounts from the new youruser-expose-image project access to image streams from the youruser-common project
`oc policy add-role-to-group -n ${RHT_OCP4_DEV_USER}-common system:image-puller system:serviceaccounts:${RHT_OCP4_DEV_USER}-expose-image`

`oc scale dc/name --replicas=3`

oc rollback dc/name

oc rollout retry dc/name

# getting default registry path 
 oc get route -n openshift-image-registry