Simple approach to creating AKS in AKS

Step1 - Setup your tfstate in Azure Storage Account.  One can use a local state file or if using Terraform Enterprise/Cloud you can use a workspace.  If you don't have TFE / TFC best to put in Azure Storage.  

Step 2 - change script tfInit to include your azure storage account name and access-key.  

Step 3 - Setup environment vars  
export TF_VAR_client_id={clientId}  
export TF_VAR_client_secret={clientSecret}  
NOTE: This is for linux shell one can also set via powershell

Step 4 - Run the terraform plan and confirm what is being created.  If you want to save the plan use terraform plan -out out.plan 

Step 5 - terraform apply out.plan 

Step 6 - echo "$(terraform output kube_config)" > ./azurek8s  

Step 7 - run installKubeCtl 

Step 8 - kubectl get nodes   
To validate cluster is up

