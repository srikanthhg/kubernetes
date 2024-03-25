Install AZ cli
* Check the below link in any browser:
```
https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt
```
AZ cli on ububtu
```
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```
Type the below command
```
az login
```
Command to create Resource group
```
az group create --location westus --resource-group MyResourceGroup
```
Below is the command to create AKS cluster 
```
az aks create --resource-group MyResourceGroup --name MyDemoCluster --location westus --generate-ssh-keys --enable-addons monitoring --load-balancer-sku standard --enable-private-cluster --private-dns-zone system --enable-aad --aad-admin-group-object-ids <AAD_Admin_Group_Object_IDs> --node-count 3 --node-vm-size Standard_DS2_v2 --node-osdisk-size 30 --node-osdisk-type Managed --nodepool-name mypool --vnet-subnet-id /subscriptions/2cab150b-4433-4b0e-95a8-fabb980b3485/resourceGroups/MyResourceGroup/providers/Microsoft.Network/virtualNetworks/myVNet/subnets/mysubnet --enable-cluster-autoscaler --min-count 3 --max-count 5 --enable-managed-identity --tags Application=cccc ContactEmail=ss@gg.com ContactName=sri Department=ecomm DistroEmail=support@ss.com 
```
```
az aks create --resource-group MyResourceGroup --name MyManagedCluster --enable-managed-identity
```
Connect to the cluster
```
az aks get-credentials --resource-group myResourceGroup --name MyManagedCluster
```
Verify the connection to your cluster using the kubectl get command. This command returns a list of the cluster nodes.
```
kubectl get nodes
```
root@Bootstrap:~# az aks update --enable-blob-driver -n MyManagedCluster -g myResourceGroup
Please make sure there is no open-source Blob CSI driver installed before enabling. (y/N): y
