## This project has two parts - the first part uses docker compose with terraform to deploy a website hosted at AWS S3 bucket. The second part, is to set up jenkins and jenkinsfile to do a simple multibranch build.



### Part I:
https://github.com/ZBr14n/Jenkins_Deploy_Website/tree/terraform_deploy_website_on_AWS


### build the docker compose file for terraform
docker-compose build terraform

### initialize terraform
docker-compose run --rm terraform init

### checks for any syntax errors and validate tf code before running
docker-compose run --rm terraform plan

### if all goes well from previous step, this will execute tf from docker
docker-compose run --rm terraform apply

### checks for the expected output 
docker-compose run --rm terraform output

### initializes aws and any other aws resources inside from docker
docker-compose run --rm aws

### copies all the files in the website folder to AWS S3 bucket for cloud storage --> afterwards you can also check that the site has been deployed
docker-compose run --rm --entrypoint aws aws s3 cp --recursive website/ s3://brianlam3633.org

### removes all files from S3 bucket first, before AWS can let you delete s3 bucket on their cloud.
docker-compose run --rm --entrypoint aws aws s3 rm --recursive s3://brianlam3633.org

### removes all remote objects manaaged by tf config
docker-compose run --rm terraform destroy


-------------------------------------------------------------------------


Part II:
https://github.com/ZBr14n/Jenkins_Deploy_Website/tree/master

1. I set up Jenkins using Linode's quick template and access it with admin credentials at http://45.79.135.232:8080/
2. From there, I manually installed git and set up SSH access to git repo for Jenkins build pipeline.
3. I was able to successfully build a Jenkinsfile.
