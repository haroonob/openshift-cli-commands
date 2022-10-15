
`oc create configmap config_map_name --from-literal key1=value1 --from-literal key2=value2`

`oc create configmap config_map_name --from-file /home/demo/conf.txt`

`oc create secret generic secret_name --from-literal username=user1 --from-literal password=mypa55w0rd`


`oc get configmap/myconf -o json` 
`oc delete configmap/myconf`

`oc set env deployment/application --from configmap/properties`

`oc set volume deployment/mydcname --add -t secret -m /path/to/mount/volume --name myvol --secret-name mysecret`

`oc set volume deployment/mydcname --add -t configmap -m /path/to/mount/volume --name myvol --configmap-name myconf`

`oc set env bc simple --list`
`oc set env bc simple npm_config_registry=http://${RHT_OCP4_NEXUS_SERVER}/repository/nodejs`


