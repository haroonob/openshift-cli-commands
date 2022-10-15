# Host to POD Commands

### Copy file from pod to host
`oc cp frontend-1-zvjhb:/var/log/httpd/error_log /tmp/frontend-server.log`

### Copy file from host to pod 
`oc cp /tmp/frontend-server.log frontend-1-zvjhb:/var/log/httpd/error_log`

### Running commands inside a pod
`oc rsh frontend-1-zvjhb ps ax`

`oc rsh quotesapi-7d76ff58f8-6j2gx bash -c 'echo > /dev/tcp/$DATABASE_SERVICE_NAME/3306 && echo OK || echo FAIL'`

### command to start an interactive shell session inside the container
`oc rsh -t frontend-1-zvjhb`

