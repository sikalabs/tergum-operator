# tergum-operator
### WIP: Not ready for use
Tergum operator is a Kubernetes operator that manages tergum backup jobs. 

## Description
Tergum operator is a Kubernetes operator that manages tergum backup jobs. 
It allows you to create, update, and delete backup jobs in a declarative way. 
The operator will ensure that the backup jobs are running as expected and will restart them if they fail.

## Getting Started
To get started, you will need to have a Kubernetes cluster running.
Tergum operator deployed on the cluster.

to specify the backup job, you will need to create a TergumBackup CR.
```yaml
apiVersion: tergum.sikalabs.com/v1alpha1
kind: Backup
metadata:
  name: backup-sample
spec:
    schedule: "* * * * *"
    config:
      {{your tergum config here}} 
```

### Prerequisites
- go version v1.21
- docker version 17.03+.
- kubectl version v1.11.3+.
- Access to a Kubernetes v1.11.3+ cluster.

### To Deploy on the cluster
**Build and push your image to the location specified by `IMG`:**

```sh
make docker-build docker-push IMG=<some-registry>/tergum-operator:tag
```

**Install the CRDs into the cluster:**

```sh
make install
```

**Deploy the Manager to the cluster with the image specified by `IMG`:**

```sh
make deploy IMG=<some-registry>/tergum-operator:tag
```

> **NOTE**: If you encounter RBAC errors, you may need to grant yourself cluster-admin 
privileges or be logged in as admin.

You can apply the samples (examples) from the config/sample:

```sh
kubectl apply -k config/samples/
```

### To Uninstall
**Delete the instances (CRs) from the cluster:**

```sh
kubectl delete -k config/samples/
```

**Delete the APIs(CRDs) from the cluster:**

```sh
make uninstall
```

**UnDeploy the controller from the cluster:**

```sh
make undeploy
```

## Contributing
We are open to contributions.
Once we have this project in a somewhat stable state, we will add more information on how to contribute.

More information can be found via the [Kubebuilder Documentation](https://book.kubebuilder.io/introduction.html)

## License

Copyright 2024 Michael Kaplan.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

