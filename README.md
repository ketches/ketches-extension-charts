# Ketches Extension Charts

This repository contains a collection of Helm charts for extending the functionality of your Kubernetes cluster.

## Usage

To use the charts from this repository, add the repository to your Helm client:

```bash
helm repo add ketches-extension-charts https://ketches.github.io/ketches-extension-charts
helm repo update
```

You can then install any of the charts by running:

```bash
helm install my-release ketches-extension-charts/<chart-name>
```

Replace `<chart-name>` with the name of the chart you want to install.

## Charts

Here are the charts available in this repository:

### LGTM Distributed

* **Description**: An umbrella chart for a distributed stack of Loki, Grafana, Tempo, and Mimir. This chart simplifies the deployment of a comprehensive observability platform.
* **Chart Version**: `2.1.0`
* **App Version**: `^7.3.9`

To install the LGTM Distributed chart, run:

```bash
helm install my-lgtm ketches-extension-charts/lgtm-distributed
```

### Velero

* **Description**: A Helm chart for Velero, a tool to back up and restore your Kubernetes cluster resources and persistent volumes.
* **Chart Version**: `5.1.0`
* **App Version**: `1.12.0`

To install the Velero chart, run:

```bash
helm install my-velero ketches-extension-charts/velero
```

## Contributing

Contributions are welcome! Please refer to the contribution guidelines for more information.
