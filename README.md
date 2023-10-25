# ketches-extension-charts

Install charts in this repository as Ketches Extensions.

Requirements:

- Ketches installed in the cluster(CRDs and controller)
- Cluster resource created

Step 0: Get the target Ketches cluster

```bash
kubectl get clusters.core.ketches.io
```

Step 1: Install the Ketches HelmRepository CRD

Example(ketches cluster is dev, so the space is ketches-admin-dev):

```bash
kubectl apply -f - <<EOF
apiVersion: core.ketches.io/v1alpha1
kind: HelmRepository
metadata:
  name: ketches-extension
  namespace: ketches-admin-dev
  labels:
    ketches.io/owned: "true"
    ketches.io/space: ketches-admin-dev
    ketches.io/helm-repository: ketches-extension
spec:
  displayName: Ketches Extension Helm Repository
  description: Ketches Extension Helm Repository, maintained by the Ketches community, contains a wealth of Ketches Extensions.
  url: https://ketches.github.io/ketches-extension-charts
EOF
```

Step 2: Install the extension

Example(ketches cluster is dev, so the space is ketches-admin-dev):

```bash
kubectl apply -f - <<EOF
apiVersion: core.ketches.io/v1alpha1
kind: Extension
metadata:
  name: velero
  namespace: ketches-admin-dev
  labels:
    ketches.io/owned: "true"
    ketches.io/space: ketches-admin-dev
    ketches.io/extension: ketches-extension
spec:
  displayName: Velero
  description: Velero is a tool to back up and restore Kubernetes cluster resources and persistent volumes.
  installType: helm
  helmInstallation: 
    repository: ketches-extension
    name: velero
    chart: ketches-extension/velero
EOF
```

Also, you can install charts in this repository with helm directly:

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

```bash
helm repo add ketches-extension https://ketches.github.io/ketches-extension-charts
```

If you had already added this repo earlier, update the repo as follows:

```bash
helm repo update ketches-extension
```

To search for charts in this repo:

```bash
helm search repo ketches-extension
```

To install the ketches-extension chart:

```bash
helm install myapp ketches-extension/myapp
```

To uninstall the chart:

```bash
helm uninstall myapp
```
