# Health Probes 
`oc set probe deployment myapp --readiness --get-url=http://:8080/healthz --period=20`

`oc set probe deployment myapp --liveness --open-tcp=3306 --period=20 --timeout-seconds=1`

`oc set probe deployment myapp --liveness --get-url=http://:8080/healthz --initial-delay-seconds=30 --success-threshold=1 --failure-threshold=3`

 oc set probe dc/quip \
--liveness --readiness --get-url=http://:8080/ready \
--initial-delay-seconds=30 --timeout-seconds=2

# examples of yaml 
livenessProbe:
  exec:
    command:1
    - cat
    - /tmp/health
  initialDelaySeconds: 15
  timeoutSeconds: 1


  readinessProbe:
  httpGet:
    path: /health1
    port: 8080
  initialDelaySeconds: 152
  timeoutSeconds: 1

  livenessProbe:
  tcpSocket:
    port: 80801
  initialDelaySeconds: 15
  timeoutSeconds: 1