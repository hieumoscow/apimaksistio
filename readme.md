export CLUSTER=istio-aks
export RESOURCE_GROUP=istio-rg
export LOCATION=eastasia

az group create --name ${RESOURCE_GROUP} --location ${LOCATION}
az aks create --resource-group ${RESOURCE_GROUP} --name ${CLUSTER} --enable-asm

# Get the credentials for the cluster
az aks get-credentials --resource-group ${RESOURCE_GROUP} --name ${CLUSTER} --admin

# create apim developer tier
az apim create --name kiwiistio-apim --resource-group ${RESOURCE_GROUP} --publisher-email hieunhu@microsoft.com --publisher-name hieunhu --sku-name Developer --location ${LOCATION}

