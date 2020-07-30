## Project Overview

In this project, we will be hosting a static website by uploading files to the S3 bucket and hosted by using Static website hosting in S3 Bucket.

---

## Setup the Enviroment

* Environment used is Ubuntu18 in cloud9.
* Jenkins with Blue Ocean Plugin & Pipeline-AWS Plugin.
* AWS account with IAM role created.
* tidy installed.

### Install Jenkins:

* `wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -`
* `sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ >> /etc/apt/sources.list'`
* `sudo apt-get update`
* `wget https://pkg.jenkins.io/debian-stable/binary/jenkins_2.204.6_all.deb`
* `sudo apt install ./jenkins_2.204.6_all.deb -y`
* `sudo systemctl start jenkins`
* `sudo systemctl enable jenkins`
* `sudo systemctl status jenkins`

### Set up AWS credentials in Jenkins:

* Click on the “Credentials” link from the sidebar.
* Click on "(global)" from the list, and then "Add credentials" from the sidebar.
* Choose "AWS Credentials" from the dropdown, add ID, description and fill in the AWS Key and Secret Access Key generated when the IAM role was created.

### Set up S3 Bucket:

* Add the Bucket Policy:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::NAME_OF_BUCKET/*"
    }
  ]
}
```
* Replace 'NAME_OF_BUCKET' with the bucket that was just created.
