# EC2 instance (self-updating web server) with a customizable message

Uses AWS::CloudFormation::Init to automate setup, including configuring the cfn-hup service to enable automatic updates when the stack changes.

Installs and run an Apache web server (httpd) and host a simple HTML page displaying a customizable message (default: "Demo message").
