mkdir -p exokustom/base
cd exokustom
helm template exoplanets \
../exochart(helm directory) > base/deployment.yaml

add kustomization.yaml file in the base directory
add following text in it.

resources:
- deployment.yaml


mkdir -p overlays/test

Create a replica_limits.yaml file in the overlays/test directory 

apiVersion: apps/v1
kind: Deployment
metadata:
  name: exoplanets-exochart
spec:
  replicas: 5
  template:
    spec:
      containers:
        - name: exochart
          resources:
            limits:
              memory: "128Mi"
              cpu: "250m"

 Create the overlays/test/kustomization.yaml     
  add following text in it 

bases:
- ../../base
patches:
- replica_limits.yaml

Apply the Test overlay to the running instance of the Exoplanets application
oc apply -k overlays/test
