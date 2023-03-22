Altschool-final-project

This repository includes all the necessary files and source codes for submitting the AltSchool Cloud Engineering 3rd Semester Exam. The project utilized various tools such as Terraform, AWS CLI, CircleCi, Prometheus, Grafana, Docker, Kubernetes, Git, and Github, as well as a domain from dottech.

The main objective of the project was to deploy two applications, namely "portfolio" and "socks shop," utilizing Kubernetes with the help of an Infrastructure as Code (IaC) tool. Terraform was used to achieve this objective. The Terraform files were organized and separated into different directories in order to optimize deployment using a CI/CD pipeline.

The "backend" directory contains the S3 bucket and DynamoDB configurations that will serve as the backend and lock for storing the Terraform deployment state. The "infrastructure" directory contains the Terraform files for deploying the necessary infrastructure to AWS, including network components such as VPC, IGW, NAT-GW, Elastic IPs, route tables and routes, subnets, and security groups. It also includes configurations for IAM roles, CloudWatch Log group, EKS node group, and EKS cluster.

The "deployment" directory contains the scripts used to deploy the two applications to the AWS infrastructure. Terraform Kubernetes manifest, deployment, and service resources were used to deploy the "portfolio" and "socks shop" apps. It also contains the configuration for the subdomains, namely "portfolio.abdulbarri.online" and "socks.abdulbarri.online."

The "monitoring" directory contains the scripts used to deploy Prometheus and Grafana to the cluster, which will be used to monitor and observe the performance and uptime of the applications.

To implement a CI/CD pipeline, CircleCI was used. The code for the CI/CD pipeline can be found in the ".circleci" folder, which contains a "config.yml" file that includes the code for the pipeline. The CI/CD pipeline has six jobs: build_docker_image, create_backend_state_store, create_infrastructure, deploy_applications, configure_monitoring

1. build_docker_image builds the Docker image for the portfolio app and uploads it to Dockerhub.
2. create_backend_state_store runs the Terraform script(s) in the terraform-files/backend directory to create an S3 backend and DynamoDB for storing and locking state. This job is triggered only if the backend branch is triggered.
3. create_infrastructure executes the Terraform script(s) in the terraform-files/infrastructure directory to create the necessary network infrastructure.
4. deploy_applications applies the Terraform script(s) in the terraform-files/deployment directory, deploying the portfolio and socks shop apps to the EKS cluster, and creates subdomains, mapping load balancers from the apps to the subdomains.
5. configure_monitoring runs the Terraform script(s) in the terraform-files/monitoring directory to deploy Prometheus and Grafana to the cluster for monitoring and performance observation.
6. destroy everything executed



