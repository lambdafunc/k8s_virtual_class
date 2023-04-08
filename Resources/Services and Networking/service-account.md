#### List service account in default namespace
```sh
kubectl get serviceaccount
```
#### Create New Namespace and Verify Service Account Creation
```sh
kubectl create namespace pinelabs
kubectl get serviceaccount -n pinelabs
```
#### Verify Secret Details
```sh
kubectl get secret -n pinelabs
kubectl get sa default -o yaml
```
#### Create a New POD
```sh
kubectl run nginx --image=nginx
kubectl exec -it nginx -- bash
cd /run/secrets/kubernetes.io/serviceaccount
ls -l
cat token
```
#### Verify Service Account Name for POD
```sh
kubectl get pod nginx -o yaml
```
#### Create New Service Account & Associate POD
```sh
kubectl create sa pinelabs
kubectl run nginx-sa --image=nginx --serviceaccount="pinelabs"
kubectl get pod nginx-sa -o yaml
```
