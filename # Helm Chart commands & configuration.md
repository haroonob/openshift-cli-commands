# Helm Chart commands & configuration changes

`helm create exochart`
`helm dependency update`
`helm install exoplanets .`



## dependencies need to add in Chart.yaml 
`dependencies:`
`- name: cockroachdb`
  `version: 6.0.4`
  `repository: https://charts.cockroachdb.com/`

## dependency.yaml 
#### add env after following lines 
`imagePullPolicy: {{ .Values.image.pullPolicy }}`

 `env:`
`   {{- range .Values.env }}`
`   - name: "{{ .name }}"`
`     value: "{{ .value }}"`
`   {{- end }}`
##### port can be change in containers

## values.yaml  
#### image repo need to update in top
env:
  - name: "DB_HOST"
    value: "exoplanets-cockroachdb"
  - name: "DB_NAME"
    value: "postgres"
  - name: "DB_USER"
    value: "root"
  - name: "DB_PORT"
    value: "26257"

You can use the helm template command to extract the object definitions from a Helm Chart into the base definition:

`helm template app-name helm-directory > base/deployment.yaml`