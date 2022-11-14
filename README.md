# **Kubernetes in local the easy way: Docker Desktop (on Mac)**

**What this is**

A step by step tutorial about one of the easiest and most straight forward ways to have a simple single-node Kubernetes cluster running in your local using [**Docker Desktop**](https://www.docker.com/products/docker-desktop) (on Mac).

Some basic knowledge of Docker and Kubernetes is expected.

**What this is not**

This is not a tutorial or an article about _what is Docker?_ or _what is Kubernetes?_. There is plenty of literature on those topics on the internet e.g:

- Docker intro from the official docs (always a good place to start): [https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)
- Kubernetes intro from the official docs: [https://kubernetes.io/docs/tutorials/kubernetes-basics/](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
- Another good one about Docker: [https://docker-curriculum.com/](https://docker-curriculum.com/)
- A nice online course about Kubernetes from Edx: [Introduction to Kubernetes](https://www.edx.org/course/introduction-to-kubernetes)

**Docker Desktop download**

**No Docker Hub option**

- If you don't have a Docker account already
- If you are not planning to publish container images
- If you prefer not to share your email address

Get the macOS Installer .dmg directly here -\>
[https://download.docker.com/mac/stable/Docker.dmg](https://download.docker.com/mac/stable/Docker.dmg)

Here for the Edge version -\> [https://download.docker.com/mac/edge/Docker.dmg](https://download.docker.com/mac/stable/Docker.dmg)

**Docker Hub option**

If you use the _standard _Docker links, for example:

[https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

[https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

They will kindly invite you to Sign In into Docker Hub, that will enable the download link, allow you to publish containers to Docker Hub, etc.

You can also do this step after the installation:

Select  **Sign in /Create Docker ID**  from the Docker Desktop menu to access your [Docker Hub](https://hub.docker.com/) account.

![](https://miro.medium.com/max/976/1*bw_ITEDpNQr7dsvrFC87xg.png)

Once logged in, you can access your Docker Hub repositories directly from the Docker Desktop menu.

**Docker Desktop installation**

1. Double-click Docker.dmg to open the installer, then drag the Docker icon to the Applications folder.

![](https://miro.medium.com/max/1400/1*9tmXy2xJZ-zxYh7u7QLdZQ.png)

1. Cmd + Space and type Docker, you should be able to see the Docker app there, just hit Enter to open it

![](https://miro.medium.com/max/1400/1*Aa4_DLAn8QJSNae8k1LyRA.png)

1. Docker will start after a few seconds

![](https://miro.medium.com/max/1368/1*TT3MADnePXIXfRDY5gz7Kw.png)

You should see a pop up like this:

![](https://miro.medium.com/max/1380/1*mZDxBJz3rUWJANIs6_dtUg.png)

You can clone the pop-up and click on the Docker icon in the top status bar

![](https://miro.medium.com/max/1188/1*UZ_gTvUB7zbeJbcyOvzTsA.png)

Top Status Bar

and go to  **Preferences ** window as shown below.

![](https://miro.medium.com/max/984/1*EjQFuXuNGTaCspXDfJ45Vg.png)

Docker menu

Then click on the  **Kubernetes ** icon.

![](https://miro.medium.com/max/1400/1*jioifvncW8RRCYD_ka347g.png)

You will notice that Kubernetes is not enabled. Simply check on the  **Enable Kubernetes ** option and then hit the  **Apply & Restart**  button as shown below:

![](https://miro.medium.com/max/1400/1*mD4h9isQUT-2FSlt-4EDlw.png)

Create a Kubernetes cluster as easy as check one checkbox

This will display a loading spinner while the Kubernetes cluster gets installed.

The installation starts. Please be patient since this could take a while depending on your network.

![](https://miro.medium.com/max/1400/1*1asY_TNWeSXO5L6AuTp9YQ.png)

The Kubernetes icon on the bottom left will turn green when the installation is done

When the installation is done you should see the same screen:

![](https://miro.medium.com/max/1400/1*MFZqj3ga0dcbqf2JzpzJaQ.png)

Note the two icons at the bottom of the window mentioning:

- **Docker**  icon is green meaning Docker is up&running
- **Kubernetes**  icon is green meaning Kubernetes cluster is up&running

![](https://miro.medium.com/max/1400/1*aKGkjvDL1uWUyY5TxEBU_g.png)

Congratulations! You now have the following:

- A standalone Kubernetes server and client, as well as Docker CLI integration.
- The Kubernetes server is a single-node cluster and is not configurable.

If you check you _About Docker_, you should see something similar to:

![](https://miro.medium.com/max/1400/1*IVH9fnW0NND_u_BxeTRM3A.png)

**Check our installation**

Let us try out a few things to ensure that we can make sense of what has got installed. Execute the following commands in a terminal:

\> kubectl version 
```
**Client Version** : version.Info{Major:"1", Minor:"14", GitVersion:"v **1.14.1**", GitCommit:"b7394102d6ef778017f2ca4046abbaa23b88c290", GitTreeState:"clean", BuildDate:"2019-04-19T22:13:37Z", GoVersion:"go1.12.4", Compiler:"gc", Platform:"darwin/amd64"} **Server Version** : version.Info{Major:"1", Minor:"19", GitVersion:"v **1.19.7**", GitCommit:"1dd5338295409edcfff11505e7bb246f0d325d15", GitTreeState:"clean", BuildDate:"2021-01-13T13:15:20Z", GoVersion:"go1.15.5", Compiler:"gc", Platform:"linux/amd64"}
```

You might have noticed that my server and client versions are different. I am using kubectl from my gCloud SDK tools and Docker for Mac, when it launched the Kubernetes cluster has been able to set the cluster context for the kubectl utility for you. So if we fire the following command:

\> kubectl config current-context
```
 docker-desktop
```

You can see that the cluster is set to  **docker-for-desktop**.

_Tip_: In case you switch between different clusters, you can always get back using the following:

$ kubectl config use-context docker-for-desktop
```
 Switched to context "docker-for-desktop"
```

Let us get some information on the cluster.

\> kubectl cluster-info
```
 Kubernetes master is running at [https://kubernetes.docker.internal:6443](https://kubernetes.docker.internal:6443/)
 KubeDNS is running at [https://kubernetes.docker.internal:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy](https://kubernetes.docker.internal:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy)To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

Let us check out the nodes in the cluster:

\> kubectl get nodes
```
 NAME STATUS ROLES AGE VERSION
 docker-desktop Ready master 21h v1.19.7
```

**Installing the Kubernetes Dashboard**

The next step that we need to do here is to install the [Kubernetes Dashboard](https://github.com/kubernetes/dashboard). We can use the Kubernetes Dashboard YAML that is available and submit the same to the Kubernetes Master as follows:

\> kubectl apply -f [kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml](kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml)

```
namespace/kubernetes-dashboard created
 serviceaccount/kubernetes-dashboard created
 service/kubernetes-dashboard created
 secret/kubernetes-dashboard-certs created
 secret/kubernetes-dashboard-csrf created
 secret/kubernetes-dashboard-key-holder created
 configmap/kubernetes-dashboard-settings created
 role.rbac.authorization.k8s.io/kubernetes-dashboard created
 clusterrole.rbac.authorization.k8s.io/kubernetes-dashboard created
 rolebinding.rbac.authorization.k8s.io/kubernetes-dashboard created
 clusterrolebinding.rbac.authorization.k8s.io/kubernetes-dashboard created
 deployment.apps/kubernetes-dashboard created
 service/dashboard-metrics-scraper created
 deployment.apps/dashboard-metrics-scraper created
```

The Dashboard application will get deployed as a Pod in the  **kubernetes-dashboard ** namespace. We can get a list of all our Pods in all namespaces via the following command:

\> kubectl get pods --all-namespaces
```
 NAMESPACE NAME READY STATUS RESTARTS AGE
 docker compose-7b7c5cbbcc-ft6zt 1/1 Running 0 2d
 docker compose-api-dbbf7c5db-8w9qw 1/1 Running 0 2d
 kube-system coredns-5c98db65d4-sj2kp 1/1 Running 0 2d
 kube-system coredns-5c98db65d4-sq2xc 1/1 Running 0 2d
 kube-system etcd-docker-desktop 1/1 Running 0 2d
 kube-system kube-apiserver-docker-desktop 1/1 Running 0 2d
 kube-system kube-controller-manager-docker-desktop 1/1 Running 0 2d
 kube-system kube-proxy-mph42 1/1 Running 0 2d
 kube-system kube-scheduler-docker-desktop 1/1 Running 0 2d
 kubernetes-dashboard dashboard-metrics-scraper-7f5767668b-w5tl4 1/1 Running 0 41h
 kubernetes-dashboard **kubernetes-dashboard** -58df6bddcb-2xbkg 1/1 Running 0 41h
```

Ensure that the Pod "_kubernetes-dashboard-_\*" is in Running state. It could take some time to change from  **ContainerCreating**  to  **Running** , so be patient.

Once it is in running state, to access Dashboard from your local workstation you must create a secure channel to your Kubernetes cluster.

**Kubectl Proxy**

_kubectl proxy_ creates a proxy server between your machine and Kubernetes API server. By default, it is only accessible locally (from the machine that started it).

Start a local proxy server.

\> kubectl proxy
```
 Starting to serve on 127.0.0.1:8001
```

Once proxy server is started you should be able to access Dashboard from your browser.

Now access you can access Dashboard at:

[http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy)

You will see the following screen:

![](https://miro.medium.com/max/1400/1*Y-Y2_S25E2KieRB1sNVqWA.png)

Login page for Kubernetes Dashboard

## Create An Authentication Token (RBAC)

To find out how to create sample user and log in follow [Creating sample user](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md) guide.

NOTE:
- Kubeconfig Authentication method does not support external identity providers or certificate-based authentication.
- Metrics-Server has to be running in the cluster for the metrics and graphs to be available. Read more about it in Integrations guide.

### Creating a Service Account
We are creating Service Account with the name admin-user in namespace kubernetes-dashboard first. `dashboard-adminuser.yaml`:
```
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard
```

To create a service account:

`$ kubectl apply -f dashboard-adminuser.yaml`
```
serviceaccount/admin-user created
```

## Getting a Bearer Token

Now we need to find the token we can use to log in. Execute the following command:

`$ kubectl -n kubernetes-dashboard create token admin-user`
```
eyJhbGciOiJSUzI1NiIsImtpZCI6IjN1S25pOG1fWHdvLXFPbm90QU1iM0U3QUpUSEpFUHpRMUdhb2lCV3JGdzQifQ.eyJhdWQiOlsiaHR0cHM6Ly9rdWJlcm5ldGVzLmRlZmF1bHQuc3ZjLmNsdXN0ZXIubG9jYWwiXSwiZXhwIjoxNjY4NDE2MTQ0LCJpYXQiOjE2Njg0MTI1NDQsImlzcyI6Imh0dHBzOi8va3ViZXJuZXRlcy5kZWZhdWx0LnN2Yy5jbHVzdGVyLmxvY2FsIiwia3ViZXJuZXRlcy5pbyI6eyJuYW1lc3BhY2UiOiJrdWJlcm5ldGVzLWRhc2hib2FyZCIsInNlcnZpY2VhY2NvdW50Ijp7Im5hbWUiOiJhZG1pbi11c2VyIiwidWlkIjoiYzU0MDkwODAtN2I3My00ZDBhLTlhYmQtYWQ3Njc4ZWVkYTI3In19LCJuYmYiOjE2Njg0MTI1NDQsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDprdWJlcm5ldGVzLWRhc2hib2FyZDphZG1pbi11c2VyIn0.JyK6KbtB_UlXKHVzkJRgoERJKCoYzHXCfUL8qAjD63WMA_j8oco6DT8m4o7SJ--sW6QSwp_HUq3dCB4WjDx9GiZ3RNuzDptcxv6I7uVCmTB9nv65zoL3QC3NV2oJNE1DxY5PlqxcOQsg6mYJOw_FHpec9k0vhBgY0YCDmsvz1x1GWyC58jdTQsUTrcUQQsNFpEDSJbass53ZDgzY05VxSnEqxwZVes6HjP-cJK6-0WTME1JQD3gcxVR7XfQfYtvW1FZNXkHli8bEJMz-rESsyft9RECzInHpYv9LGYpmcbLd1LZZjFYr7mdLzxlsiM_zCWNoPo-NaPzPfgts3E65Dg
```

Copy & paste that token into the field and click  **Sign In ** to login, the dashboard will show as below:

![](https://miro.medium.com/max/1400/1*LWAiiOJMuMsLkN6S36llDg.png)

**Let's Play!**

Let us proceed now to running a simple [Nginx container](https://hub.docker.com/_/nginx) to see the whole thing in action:

First things first, setup your command line for productivity:

1. Kubectl autocomplete

Bash `source <(kubectl completion bash)`

Zsh `source <(kubectl completion zsh)`

2. Alias for kubectl

Alias to type less (lazy is good) and it will also work with completion:

```
alias k=kubectl
complete -F __start_kubectl k
```

Now let's create our first namespace:

\> k create namespace my-demo
```
 namespace/my-demo created
```

To easy work within our new context let's make it the default:

```
kubectl config set-context --current --namespace=my-demo
```

TIP: create an alias with this, to be able to check contexts easily:

```
alias kn='kubectl config set-context --current --namespace
```

so now you can do

`kn my-demo` or `kn default`

We are going to use the run command as shown below:

```
k run nginx --image=nginx --port=80 --restart=Never
```

This creates a Pod ([https://kubernetes.io/docs/reference/kubectl/conventions/#generators](https://kubernetes.io/docs/reference/kubectl/conventions/#generators)) and we can investigate into the Pod that gets created, which will run the container:

\> k get pods
```
 NAME READY STATUS RESTARTS AGE
 nginx 0/1 ContainerCreating 0 4s
```

You can see that the STATUS column value is  **ContainerCreating**.

If we wait for a while, the Pod will eventually get created and it will ready as the command below shows:

\> k get pods
```
 NAME READY STATUS RESTARTS AGE
 nginx 1/1 Running 0 14s
```

Now, let us go back to the Dashboard and get to the Pods via the  **Pods**  link in the Workloads as shown below:

![](https://miro.medium.com/max/1400/1*ce98Pun7cZMLU9tSXSncAw.png)

Click on the Pod and you can get various details on it as given below:

You can see that it has been given some default labels. You can see its IP address. It is part of the node named  **docker-for-desktop**.

There are some interesting links that you will find on this page as shown below, via which you can directly EXEC into the pods or see the logs too.

![](https://miro.medium.com/max/440/1*zlGNC7ul5acu4jbrYIb2sA.png)

"View Logs" and "EXEC into pod" buttons

We could have got the Node and Pod details via a variety of  **kubectl describe node/pod**  commands and we can still do that. An example of that is shown below:

`k describe pod nginx`
```
 Name: nginx
 Namespace: my-demo
 Priority: 0
 PriorityClassName: \<none\>
 Node: docker-desktop/192.168.65.3
 Start Time: Sun, 02 Feb 2020 09:34:07 +0100
 Labels: run=nginx
 Annotations: \<none\>
 Status: Running
 IP: 10.1.0.9
 Containers:
 nginx:
 Container ID: docker://10f7fa716e60e7c010adb2e67d1488d4dca11cd1601793ced8847cc35f6f413f
 Image: nginx
 Image ID: docker-pullable://nginx@sha256:4da336e712e183bff64a09a54a727c14eb9c9d7610ce79c6fe30738b5a82cc10
 Port: 80/TCP
 Host Port: 0/TCP
 State: Running
 Started: Sun, 02 Feb 2020 09:34:10 +0100
 Ready: True
 Restart Count: 0
 Environment: \<none\>
 Mounts:
 /var/run/secrets/kubernetes.io/serviceaccount from default-token-9v699 (ro)
 Conditions:
 Type Status
 Initialized True
 Ready True
 ContainersReady True
 PodScheduled True
 Volumes:
 default-token-9v699:
 Type: Secret (a volume populated by a Secret)
 SecretName: default-token-9v699
 Optional: false
 QoS Class: BestEffort
 Node-Selectors: \<none\>
 Tolerations: node.kubernetes.io/not-ready:NoExecute for 300s
 node.kubernetes.io/unreachable:NoExecute for 300s
 Events:
 Type Reason Age From Message
 ---- ------ ---- ---- -------
 Normal Scheduled 25h default-scheduler Successfully assigned my-demo/nginx to docker-desktop
 Normal Pulling 25h kubelet, docker-desktop Pulling image "nginx"
 Normal Pulled 25h kubelet, docker-desktop Successfully pulled image "nginx"
 Normal Created 25h kubelet, docker-desktop Created container nginx
 Normal Started 25h kubelet, docker-desktop Started container nginx
```

**Expose a Service**

It is time now to expose our basic Nginx deployment as a service. We can use the command shown below:

\> k expose pod nginx --type=NodePort
```
 service/nginx exposed
```

If we visit the Dashboard at this point and go to the Services section, we can see our  **nginx ** service entry.

![](https://miro.medium.com/max/1400/1*a7F4N3bfwOR4bHMZceCP-A.png)

Alternately, we can use the terminal too, to check it out:

\> k get svc
```
 NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
 nginx NodePort 10.104.91.251 \<none\> 80:31338/TCP 4s
```

and

\> k describe service nginx
```
 Name: nginx
 Namespace: my-demo
 Labels: run=nginx
 Annotations: \<none\>
 Selector: run=nginx
 Type: NodePort
 IP: 10.104.91.251
 LoadBalancer Ingress: localhost
 Port: \<unset\> 80/TCP
 TargetPort: 80/TCP
 NodePort: \<unset\> **31338** /TCP
 Endpoints: 10.1.0.9:80
 Session Affinity: None
 External Traffic Policy: Cluster
 Events: \<none\>
```

You can now visit: [localhost:31338](http://localhost:31338/) and you will see nginx welcome page:

![](https://miro.medium.com/max/1400/1*MRtVYiyauGDsIXGX7a-RDQ.png)

Nginx welcome page

**Conclusion**

If you want to have a Kubernetes cluster running in your local in a quick and easy way I hope this blog post helps you with Kubernetes and Docker Desktop for Mac.

Of course, there are other alternatives for running Kubernetes in your local machine, just to mention some of them:

**Minikube** : [https://github.com/kubernetes/minikube](https://github.com/kubernetes/minikube)

**Minishift**  (from Openshift): [https://github.com/MiniShift/minishift](https://github.com/MiniShift/minishift)

**MicroK8s** : [https://microk8s.io/](https://microk8s.io/)

**k3s** : [https://k3s.io/](https://k3s.io/)

**k3sup** : [https://github.com/alexellis/k3sup](https://github.com/alexellis/k3sup)

**k3d** : [https://github.com/rancher/k3d](https://github.com/rancher/k3d)

**kind**  (kubernetes in Docker): [https://kind.sigs.k8s.io/](https://kind.sigs.k8s.io/)

I also used a lot of online resources at the beginning just to play with it and practice some basic concepts, I like especially:

- **Katacoda** : [They](https://www.katacoda.com/kubernetes) have several scenarios and also a _playground_ cluster with master and one node to play with: [https://www.katacoda.com/courses/kubernetes/playground](https://www.katacoda.com/courses/kubernetes/playground)


**Sources**
- https://medium.com/backbase/kubernetes-in-local-the-easy-way-f8ef2b98be68