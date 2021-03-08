# kefir-on-k8s
## Provisioning a kubernetes cluster using Terraform
~~~
cd terraform
terraform init
terraform plan
terraform apply
~~~
![image](https://user-images.githubusercontent.com/53195216/110395583-72ca6200-807f-11eb-82bd-adfed2c47ae5.png)
![image](https://user-images.githubusercontent.com/53195216/110395707-ae652c00-807f-11eb-9714-2608df1ba1ff.png)
kubernetes configuration file with credentials will be automatically geneated and available in the same directory
![image](https://user-images.githubusercontent.com/53195216/110396655-72cb6180-8081-11eb-92e2-6ef87d69ae65.png)
Inspect the cluster pods using the generated kubeconfig file:
~~~
kubectl get pods --all-namespaces --kubeconfig=kubeconfig-prod
~~~
to not prefix the KUBECONFIG environment variable to every command, it can be exported:
~~~
export KUBECONFIG="${PWD}/kubeconfig-dev"
kubectl get pods --all-namespaces
~~~
![image](https://user-images.githubusercontent.com/53195216/110397117-4fed7d00-8082-11eb-9d5e-889d7a43215c.png)
## Deploy application by Helm
~~~
helm install app app-HelmChart/
~~~
