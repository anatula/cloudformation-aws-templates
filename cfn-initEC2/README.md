# EC2 instance with a web server hosting a customizable HTML page

- Installs the Apache web server (httpd) using cfn-init
- Creates an HTML page (/var/www/html/index.html) with a customizable message (default: "Demo 1")
- cfn-init configures the instance during launch.
- cfn-signal notifies CloudFormation when the instance setup is complete.
