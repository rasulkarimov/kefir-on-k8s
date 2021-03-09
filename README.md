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
kubectl get pods --all-namespaces --kubeconfig=kubeconfig-dev
~~~
![image](https://user-images.githubusercontent.com/53195216/110397311-af4b8d00-8082-11eb-9610-29e4bb834c1e.png)
  
to not prefix the KUBECONFIG environment variable to every command, it can be exported:
~~~
export KUBECONFIG="${PWD}/kubeconfig-dev"
kubectl get pods --all-namespaces
~~~
## Deploy application by Helm  
inspect values.yaml file in "app-HelmChart" directory  
![image](https://user-images.githubusercontent.com/53195216/110397510-09e4e900-8083-11eb-94aa-b49c8725b52a.png)  
Deploy application using Helm:
~~~
helm install app app-HelmChart/
~~~
![image](https://user-images.githubusercontent.com/53195216/110397649-503a4800-8083-11eb-81a4-c5b3bd925cb7.png) 
Inspect that pods are created:
![image](https://user-images.githubusercontent.com/53195216/110397843-ab6c3a80-8083-11eb-94b3-edae55a1b0c6.png) 
Optain external IP of loadBalancer:
![image](https://user-images.githubusercontent.com/53195216/110397998-f8501100-8083-11eb-9020-cd4bea04ae0b.png) 
Check availability:
![image](https://user-images.githubusercontent.com/53195216/110398061-1b7ac080-8084-11eb-9017-3ca52d5b1d39.png)


