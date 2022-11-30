# Steps to import image as stream from Quay.io or other repository 


pre condition Image should be exist 

For public images

`oc import-image myis --confirm --from registry.acme.example.com:5000/acme/awesome --insecure`

For private images

### 1) create secret
  -- login repo using podman 
  `oc create secret generic nameofsecret --from-file .dockerconfigjson=${XDG_RUNTIME_DIR}/containers/auth.json --type kubernetes.io/dockerconfigjson`
### 2) link secrete 
`oc secretes link builder  nameofsecret` 

### 2) link secrete with new-app 
`oc secretes link default nameofsecret --for=pull `


### 3) Import Image 
`oc import-image myis --confirm --from registry.acme.example.com:5000/acme/awesome`
 `oc new-app --name hello -i myis`
### 
`oc policy add-role-to-group -n ${RHT_OCP4_DEV_USER}-common system:image-puller system:serviceaccounts:${RHT_OCP4_DEV_USER}-expose-image`


## remove old is  
`oc delete is image-name`