# Use Base Image 
`oc new-app php~http://gitserver.example.com/mygitrepo`
`oc new-app -i php http://gitserver.example.com/mygitrepo`

### Create New with build env param
`oc new-app --name greet --build-env npm_config_registry=http://${RHT_OCP4_NEXUS_SERVER}/repository/nodejs  nodejs:12~https://github.com/${RHT_OCP4_GITHUB_USER}/DO288-apps#source-build  --context-dir nodejs-helloworld`

# Pass environment variables  
`oc new-app mysql -e MYSQL_USER=user -e MYSQL_PASSWORD=pass -e MYSQL_DATABASE=testdb -l db=mysql`

# creating new app from external repo 
`oc new-app --name hola quay.io/${RHT_OCP4_QUAY_USER}/do288-apache`

# create new app with deployment config
`oc new-app --as-deployment-config --name hello -i php --code http://gitserver.example.com/mygitrepo`