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
helm add repo <repo-name> <https://repo-path>
```
We can see the repo installed with
```
helm search list
```
### Installing the charts.
After the chart is installed, we need to find the chart we want to install.
```
helm search repo <chart-name>
helm install <the project name> <repo-name>/<chartname> 
```

### Verifying the result
When we execute the install, with the `kubectl get pods -w` we can see the creation of two pods, a wordpress pod and a mariadb pod. We can use `kubectl get services` to see a service is created. With the `kubectl describe services <servicename>` you can see the container port 80 is open.
`kubectl port-forward service/<servicename> 8000:80` and in your browser paste this url: `localhost:8000` you will see a nginx UI.

### Deleting the app.
In the end, you can delete all resource created with only one command.
```
kubectl uninstall <the project name>
```
After this, we can execute the commands in **Verifying the result** and we see all resource created is deleted. 

### Commands used on helm
<table>
<tr>
<th> helm search hub </th>
<th> helm search repo </th>
</tr>
<tr>
<th> Search all repo who is storage on the helm artifact hub </th>
<th> Search all repo installed on your computer</th>
</tr>
</table>