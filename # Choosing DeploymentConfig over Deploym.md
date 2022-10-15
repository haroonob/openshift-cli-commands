# Choosing DeploymentConfig over Deployments
The Deployment resource does not support custom strategies.

The Deployment resource enables you to define container lifecycle hooks, such as PostStart and PreStop, which are similar to the lifecycle hooks provided by the DeploymentConfig resource. However, the Deployment container lifecycle hooks are not guaranteed to be executed before the ENTRYPOINT command of the container pod.

# Rolling
Use a rolling deployment strategy when:

You require no downtime during an application update.

Your application supports running an older version and a newer version at the same time.

# Recreate
In this strategy, Red Hat OpenShift first stops all the pods that are currently running and only then starts up pods with the new version of the application. This strategy incurs downtime because, for a brief period, no instances of your application are running.

Use a recreate deployment strategy when:

Your application does not support running an older version and a newer version at the same time.

Your application uses a persistent volume with RWO (ReadWriteOnce) access mode, which does not allow writes from multiple pods.