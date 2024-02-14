## What is helm?
In the past, when we needed to install a program, we had to install all dependencies and management to not cause any conflict. But after some years, package manager are created, and now we can install a program with only one command.
- for Debian are *apt*
- In Arch we have the *pacman*
- MacOs use *homebrew* 
helm work with the same idea. When we need to create a wordpress, we have to create our frontend, backend, secrets, config map, namespace, services and endpoints. With helm we can only execute one command to install and configure all the resources with the help of a chart.
```
helm install chart-name
```
But, before we can run the charts, it's necessary to add the repository to our helm. We can search then with the commands
```
helm search hub
```
### Adding a remote repo to our repo list
In the ubuntu, when we desire to install a package, the package manager will look at /var/lib/apt to find a trusted repository to install our file. In helm has no difference. Before we install any charts we need to add a repo to our trusted list with the command:
```
helm repo add bitnami https://raw.githubusercontent.com/bitnami/charts/archive-full-index/bitnami
```
We can see the repo installed with
```
helm search repo
```
### Installing the charts.
After the chart is installed, we need to find the chart we want to install.
```
helm search wordpress
helm install wordpress bitnami/wordpress -n wordpress 
```

### Verifying the result
When we execute the install, with the `kubectl get pods -w` we can see the creation of two pods, a wordpress pod and a mariadb pod. We can use `kubectl get services` to see if the service is created. With the `kubectl describe services <servicename>` 

### Access our applications
If we run the following command, we can see the url we need to access our application. 
```
minikube service wordpress -n wordpress --url
# You will recieve an URL, after you click, the browser will be open and a worpress app will be showed
```

### Deleting the app.
In the end, you can delete all resources created with only one command.
```
kubectl uninstall wordpress
```
After this, we can execute the commands in **Verifying the result** and we see all resource created is deleted. 

### Commands used on helm
<table>
<tr>
<th> helm search hub </th>
<th> Search all repo who is storage on the helm artifact hub </th>
</tr>
<tr>
<th> helm search repo </th>
<th> Search all repo installed on your computer</th>
</tr>
<tr>
<th> helm install chart repo/chart </th>
<th> create all resource necessary to run your application </th>
</tr>
<tr>
<th> helm unistall chart </th>
<th> delete all resource used </th>
</tr>
</table>
