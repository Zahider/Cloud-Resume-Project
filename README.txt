Cloud hosted resume 

GitHub Actions workflow triggers a deployment process to an EC2 instance when there is a push to the main branch, checking out the repository, deploying files via SSH, and executing remote SSH commands to set up Apache and move files to the web server's root directory.

Steps taken to automate CI/CD through GitHub actions.
1. Log-in to the AWS console and create an EC2 instance. Select Ubuntu as the OS.
2. Create a new key pair for this EC2, this will be used later on for accessing the instance. 
3. Create a new security group and allow HTTPS traffic from the internet for security as it encrypts data exchange between a user and the web server. A premade security group can also be used. Just ensure for inbound rules the following ports are added: HTTP 80, HTTPS 443 and SSH 22.
4. Now enter your GitHub repository, go to settings and create a new secret. Paste your previously created Key Pair in the secret box. This will let GitHub actions access and update your website on your behalf everytime there are changes made to your repository.
5. Head over to your EC2 instance anc copy the public IPv4 DNS address. Now create another secret and use the address as another secret. This is so GitHub knows where to access the instance.
6. Create another secret, named USERNAME. Since we are using Ubuntu as our OS, the username will be preset to ubuntu.
7. Create one last secret named TARGET_DIR which is the target directory, set as home.
8. Create a new GitHub actions workflow by creating a new .yaml  file in your repository. This GitHub Actions workflow triggers a deployment process to an EC2 instance when there is a push to the main branch, checking out the repository, deploying files via SSH, and executing remote SSH commands to set up Apache and move files to the web server's root directory.
9. Copy your public IPv4 address of the EC2 instance and see your website live. Now any changes made on the github repository will be updated immediately.

******NOTE****** Instance and VPC has been terminated to avoid charges
Website is now statically hosted in an S3 bucket and can be accessed at zrcovert.com
