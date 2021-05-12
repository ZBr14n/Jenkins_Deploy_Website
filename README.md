## This project has two parts - the first part uses docker compose with terraform to deploy a website hosted at AWS S3 bucket. The second part, is to set up jenkins and jenkinsfile to do a simple multibranch build.


### Part II:
https://github.com/ZBr14n/Jenkins_Deploy_Website/tree/master

1. I set up Jenkins using Linode's quick template and access it with admin credentials at http://45.79.135.232:8080/
2. From there, I manually installed git and set up SSH access to git repo for Jenkins build pipeline.
3. I was able to successfully build a Jenkinsfile.
