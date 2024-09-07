# Deploy RAG to Kubernertes with KServe

Step 1 ) Create a cluster, e.g. GKE, by kind create cluster 
Step 2 ) Install Cert Manager, Istio and KubeFlow componets such as KNative following below instructions 
https://github.com/kubeflow/manifests?tab=readme-ov-file#install-individual-components)
Step 3 ) Initialize a Python project by Poetry and add dependencies in pyproject.toml 
Step 4 ) Subclass Kserve.Model,buildpack the custom model by Docker and deploy to your Kubernetes cluster
