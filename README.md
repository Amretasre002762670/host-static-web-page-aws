# host-static-web-page-aws
This is a static web page that will be hosted in aws

## Commands to run in EC2 instance to install the static web application into the instance
### Switch to the root user to gain full administrative privileges
```sudo su```

### Update all installed packages to their latest versions
```yum update -y```

### Install Apache HTTP Server
```yum install -y httpd```

### Change the current working directory to the Apache web root
```cd /var/www/html```

### Install Git
```yum install git -y```

### Clone the project GitHub repository to the current directory
```git clone [github_url_of_this_project](https://github.com/Amretasre002762670/host-static-web-page-aws.git)```

### Copy all files, including hidden ones, from the cloned repository to the Apache web root
```cp -R host-static-web-page-aws/. /var/www/html/```

### Remove the cloned repository directory to clean up unnecessary files
```rm -rf host-static-web-page-aws```

### Enable the Apache HTTP Server to start automatically at system boot
```systemctl enable httpd``` 

### Start the Apache HTTP Server to serve web content
```systemctl start httpd```

