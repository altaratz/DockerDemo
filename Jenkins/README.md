Jenkins on Docker example
This project builds a jenkins master on docker, with a predefined job and plugins

Build docker image:
docker build -t jenkins .

Run docker container:
docker run -d -p 8080:8080 -p 50000:50000 jenkins

Advanced:
Run Jenkins with persistency and host docker :
docker run -d -p 8080:8080 -p 50000:50000 -v <Local folder>:/var/jenkins_home/ -v /var/run/docker.sock:/var/run/docker.sock jenkins

Run Jenkins with JAVA_OPTS
see full list here

Example:
docker run -d -p 8080:8080 -p 50000:50000 --env JAVA_OPTS="-Dhudson.footerURL=http://mycompany.com -Djenkins.install.runSetupWizard=false" jenkins

jenkins authentication
Default: user: admin pass: admin
Recommended: Google login plugin .
See Google OAuth configuration here .
Note: Requires setting the URL of jenkins correctly in Jenkins Location > Jenkins URL first .
Persistency and Backup
Run docker with shared volumes on the hosts (on AWS use EBS) .
Example:
docker run -d -p 8080:8080 -p 50000:50000 -v <Host persistent folder>:/var/jenkins_home/ jenkins - Backup and auditing:
-- Backup configuration with git
-- Backup configuration to s3
