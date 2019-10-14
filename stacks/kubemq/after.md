
### Step 1 - Point to your Cluster

Before we can do anything, we need to ensure you have access to a Kubernetes cluster you have deployed before

1. Get list of your clusters
```bash
doctl k8s cluster list
```

2. Save your kube config to your kubectl config file
```bash
doctl k8s cluster kubeconfig save <your created cluster name>
```

3. Get your context list and look for your cluster context name
```bash
kubectl config get-contexts
```

4. Switch to desired context

```bash
kubectl config set-context <your-cluster-context-name>
```

### Step 2 - Get KubeMQ CLI - kubemqctl

Kubemqctl is a CLI (Command Line Interface) tool to deploy and manage KubeMQ clusters.

#### macOS / Linux

```bash
curl -sL https://get.kubemq.io/install | sh 
```
#### Windows

##### Option 1:

- [Download the latest kubemqctl.exe](https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl.exe).
- Place the file under e.g. `C:\Program Files\kubemqctl\kubemqctl.exe`
- Add that directory to your system path to access it from any command prompt

##### Option 2:
Run in PowerShell as administrator:

```powershell
New-Item -ItemType Directory 'C:\Program Files\kubemqctl'
Invoke-WebRequest https://github.com/kubemq-io/kubemqctl/releases/download/latest/kubemqctl.exe -OutFile 'C:\Program Files\kubemqctl\kubemqctl.exe'
[Environment]::SetEnvironmentVariable('Path', [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine) + ';C:\Program Files\kubemqctl', [EnvironmentVariableTarget]::Machine)
$env:Path += ';C:\Program Files\kubemqctl'
```


### Step 3 - Send 'hello-world'

After you have created a KubeMQ cluster, you can send hello-world message to q1 queue channel.

``` bash
kubemqctl queue send q1 hello-world
```

### Step 4 - Get 'hello-world'

After you have sent a message to q1 queue channel, you can retrieve the message like this:

``` bash
kubemqctl queue receive q1
```


### Step 5 - Register your Cluster

- Run the following command:

```bash
kubemqctl cluster register
```

- Select the KubeMQ cluster to register (kubemq\kubemq-cluster)
- Fill the required information:
  - Name
  - Your email address
  - Password


- Check your email account and complete your registration

[Checkout out our docs for detailed steps](https://docs.kubemq.io/operations/register.html)

