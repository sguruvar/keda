# KEDA — AMP External Scaler Contribution

Fork of [kedacore/keda](https://github.com/kedacore/keda) for CNCF upstream contribution.

## Contribution: Amazon Managed Prometheus (AMP) External Scaler

**Merged PR:** [kedacore/keda#5315](https://github.com/kedacore/keda/pull/5315)
**AWS Blog:** [Autoscaling Kubernetes workloads with KEDA using Amazon Managed Service for Prometheus metrics](https://aws.amazon.com/blogs/mt/autoscaling-kubernetes-workloads-with-keda-using-amazon-managed-service-for-prometheus-metrics/)

Added a native KEDA scaler for Amazon Managed Prometheus — enables Kubernetes
workloads to autoscale on AMP metrics without running self-managed Prometheus.

### What was built
- `aws_managed_prometheus` scaler with AWS SigV4 authentication
- Pod identity (IRSA) support for EKS deployments
- End-to-end tests validating scaler behavior
- AWS SDK v2 integration

### Why it matters
Before this scaler, teams using AMP on EKS had to run a self-managed Prometheus
instance just to feed metrics to KEDA — defeating the purpose of a managed service.
This scaler lets KEDA query AMP directly via IAM, removing the intermediate hop.

### Real-world use
The AMP scaler powers event-driven autoscaling in the
[multi-agent-workflow](https://github.com/sguruvar/multi-agent-workflow) platform —
GPU inference workloads scale on queue depth metrics stored in AMP.

---

For the full KEDA project, see [kedacore/keda](https://github.com/kedacore/keda).
