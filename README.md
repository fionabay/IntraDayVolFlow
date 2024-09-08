# Deploy RAG to Kubernetes with KServe

- Step 1 ) Create a cluster, e.g. GKE, by
          kind create cluster --config=kind-local.yaml
- Step 2 ) Install Cert Manager, Istio and KubeFlow componets such as KNative following below instructions 
          https://github.com/kubeflow/manifests?tab=readme-ov-file#install-individual-components)
- Step 3 ) Initialize a Python project by Poetry and add dependencies in pyproject.toml 
- Step 4 ) Subclass Kserve.Model,buildpack the custom model to a Docker image 
- Step 5)  Deploy by kubectl apply -f deployment.yaml
- Step 6)  In a bad scenario, one probably will see Internal error occurred: failed calling webhook "inferenceservice.kserve-webhook-server.defaulter": failed to call webhook: Post "https://kserve-webhook-server-service.kserve.svc:443/mutate-serving-kserve-io-v1beta1-inferenceservice?timeout=10s": dial tcp X.X.X.192:443: connect: connection refused
- Step 7) A quick workaround is to delete webhook config as below
  - kubectl delete mutatingwebhookconfigurations.admissionregistra  inferenceservice.serving.kserve.io
  - kubectl delete validatingwebhookconfigurations.admissionregistration.k8s.io  inferenceservice.serving.kserve.io
