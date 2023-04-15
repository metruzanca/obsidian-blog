### 1. Install gcloud cli, kubectl, helm

- `gcloud` is used to create resources on gcp
- `kubectl` is to control the k8s cluster
- `heml` is the k8s package manager.

```
brew install google-cloud-sdk kubectl
```

### 2. Initialize the CLI (auth etc)

```
gcloud init
```

#### 2.5 Install gcloud plugins

```
gcloud components install gke-gcloud-auth-plugin
```

### 3. Get kubectl credentials from gcloud

```
gcloud container clusters list
```

Copy the name and location(region) from that list

```
gcloud container clusters get-credentials <name> --region=<region>
```

This should create a config at `$HOME/.kube/config`

### 4. Test k8s config

```
kubectl cluster-info
```