# Kubernetes

## Pods 

### Get pods

    kubectl get pods

### Pod details (memory / events)

    kubectl describe pods {pod_name}

## Logs

### XL log

    kubectl logs -f rsyslog-xx

### rsyslog

    kubectl exec -it rsyslog-xx -- /bin/bash
    kubectl exec -it $(kubectl get pods | awk '/rsyslog/ {print $1}') – /bin/bash

