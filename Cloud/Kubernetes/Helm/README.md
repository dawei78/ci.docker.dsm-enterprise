
This directory contains files to create a Helm chart for DSM.

1. Package files to chart then you will get a tgz file dsm-0.1.0.tgz in current directory:
```Bash
Helm package dsm
```
2. Install chart in  Kubernetes:
```Bash
Helm install --set setup.dsmAdmin=<admin user name> --set setup.dsmAdminPwd=<admin password> --set setup.repoDB.IP=<RepoDB IP address> --set setup.repoDB.port=<RepoDB port> --set setup.repoDB.user=<RepoDB user name> --set setup.repoDB.pwd=<RepoDB password> --set setup.repoDB.name=<RepoDB name>  --namespace <NAMESPACE> dsm-0.1.0.tgz
```
    To override values in a chart, use either the –values flag and pass in a file or use the --set flag and pass configuration from the command line.
    Refer to https://docs.helm.sh/helm/#helm-install
  
3. Then you can see release created and get release name:
```Bash
Helm ls
```
4. You can check service to get node port:
```Bash
kubectl describe svc <RELEASENAME-dsm>
```
5. After a while you can access DSM by http://\<K8s-node-ip\>:\<Nodeport\>
