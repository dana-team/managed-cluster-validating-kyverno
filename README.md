# managed-cluster-validating-kyverno

- [clusterlogging-validation](https://github.com/dana-team/managed-cluster-validating-kyverno/blob/main/allow-log-retention-outside-range.yaml): Managed OpenShift Customers may set log retention outside the allowed range of 0-7 days
- [scc-validation](https://github.com/dana-team/managed-cluster-validating-kyverno/blob/main/block-modify-default-sccs.yaml): Managed OpenShift Customers may not modify the following default SCCs: [anyuid hostaccess hostmount-anyuid hostnetwork node-exporter nonroot privileged restricted]
- [regular-user-validation](https://github.com/dana-team/managed-cluster-validating-kyverno/blob/main/prevent-object-management.yaml): Managed OpenShift customers may not manage any objects in the following APIgroups [autoscaling.openshift.io config.openshift.io operator.openshift.io network.openshift.io machine.openshift.io admissionregistration.k8s.io splunkforwarder.managed.openshift.io upgrade.managed.openshift.io ocmagent.managed.openshift.io cloudcredential.openshift.io addons.managed.openshift.io cloudingress.managed.openshift.io managed.openshift.io], nor may Managed OpenShift customers alter the APIServer, KubeAPIServer, OpenShiftAPIServer, ClusterVersion, Node or SubjectPermission objects.
- [pod-validation](https://github.com/dana-team/managed-cluster-validating-kyverno/blob/main/allow-pod-tolerations-on-infra-and-master-nodes.yaml): Managed OpenShift Customers may use tolerations on Pods that could cause those Pods to be scheduled on infra or master nodes.
- [namespace-validation](https://github.com/dana-team/managed-cluster-validating-kyverno/blob/main/prevent-modify-namespaces-and-labels.yaml): Managed OpenShift Customers may not modify namespaces specified in the [openshift-monitoring/addons-namespaces openshift-monitoring/managed-namespaces openshift-monitoring/ocp-namespaces] ConfigMaps because customer workloads should be placed in customer-created namespaces. Customers may not create namespaces identified by this regular expression (^com$|^io$|^in$) because it could interfere with critical DNS resolution. Additionally, customers may not set or change the values of these Namespace labels [managed.openshift.io/storage-pv-quota-exempt managed.openshift.io/service-lb-quota-exempt].
- [techpreviewnoupgrade-validation](https://github.com/dana-team/managed-cluster-validating-kyverno/blob/main/prevent-techpreviewnoupgrade-featuregate.yaml): Managed OpenShift Customers may not use TechPreviewNoUpgrade FeatureGate that could prevent any future ability to do a y-stream upgrade to their clusters.