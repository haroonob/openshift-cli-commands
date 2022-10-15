
# Creating External Service
`oc create service externalname $name  external-name $host`

# ConfigMap Yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: db-config
data:
  DATABASE_USER: todoapp
  DATABASE_PASSWORD: redhat123
  DATABASE_SVC_HOSTNAME: tododb
  DATABASE_NAME: todo
# configuration for inject env in app
  spec:
  template:
    spec:
      containers:
      - envFrom:
        - configMapRef:
            name: db-config

 # maven jkube goals
 ## build deploy
 `mvn clean compile package oc:build oc:resource oc:apply`
 ## deploy after changes
 `mvn oc:resource oc:apply`

