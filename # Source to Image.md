# Source to Image 

### Copy the S2I scripts to the appropriate location in the builder image
`COPY ./s2i/bin/ /usr/libexec/s2i`
### Build your base image
`podman build -t s2i-do288-go . --layers=false`

### Build a Dockerfile for an application container image that combines the S2I builder image and the application source code locally
`s2i build source_code_of_child_app image_name app_name --as-dockerfile /PATH_OF_DOCKER_FILE/Dockerfile`

#Customizing existing s2i 
Customizing existing s2i base image can be done simple adding *.s2i/bin* folder and the customization in following files 
1. assemble 
2. run 
3. usage 

## assemble file
cp -Rf /tmp/src/*.html ./
## docker file
COPY ./s2i/bin/ /usr/libexec/s2i
##
s2i create s2i-do288-httpd s2i-do288-httpd