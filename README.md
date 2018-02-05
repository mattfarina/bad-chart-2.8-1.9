# Demo of CRD API Machinery Bug Impacting Helm

There is a [Helm issue](https://github.com/kubernetes/helm/issues/3382) about a
bug affecting upgrades of applications using CRDs. This issue appears to be one
for [API Machinery](https://github.com/kubernetes/kubernetes/issues/58017).

This repository provides an example that can be used to test the situation.

Here are the steps:

1. Get Helm 2.8 and kubectl for Kubernetes 1.9
2. Install the CRD with `kubectl`. The command from the root of this repo is
   `kubectl apply -f crd-ex.yaml`.
3. Install the chart with helm. For example, use
   `helm upgrade --reset-values --install --namespace default foo .`
4. Alter the metadata. Just change anything in that (e.g., modify a label like the version)
5. Upgrade the chart. Use can use the command
   `helm upgrade --reset-values --install --namespace default foo .`