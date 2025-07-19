# CustomDomain
This repository is used to create a folder structure and scripts for creating an S3 bucket and access to via API gateway.
It uses several independent submodules and Cloudformation templates.
Steps for the CustomDomain template:
 
## 1) Create basic structure
AWS CloudFormation Stack files for the solution
```
git submodule add https://github.com/Pierre-AmultisDev/aws_cfn_s3_via_apigw stack_templates
```

Scripts to create and manage the CloudFormation stack
```
git submodule add https://github.com/Pierre-AmultisDev/aws_cfn_stack_scripts stack_scripts
```

Scripts to test the CloudFormation stack
```
git submodule add https://github.com/Pierre-AmultisDev/aws_cfn_test_scripts stack_tests
```

## 2) Set files for this project
```
_AWS-region.txt      AWS region where to create stack
_AWS-profile.txt     AWS profile name used to create stack 
_AWS_costcenter.txt  costcenter tag to use when stack is created 
```
## 3) Create the CustomDomain stack using the Cloudformation script
The stack will be created but CloudFormation will wait until domain name is validated

## 4) Validate custom domain
This CloudFormation template generates a ACM certificate but the linked domainname needs to be validated.
[You can find the certificates here:](https://eu-central-1.console.aws.amazon.com/acm/home?region=eu-central-1#/certificates/list)
![CNAME settings for ACM](./assets/img/AWS_ACM_CNAME.png)
Add the info from to domain DNS server. Don't forget the . at both ends
![DNS CNAME settings for ACM](./assets/img/DNS_entry.png)
It might take some time before the (sub)domain is present in DNS and before ACM validates it.

## 5) Link custom domain name to API GW
When the certificate is verified, the domain name has to be linked to api url
[You can find that info here:](https://eu-central-1.console.aws.amazon.com/apigateway/main/publish/domain-names?region=eu-central-1)
![CNAME settings for domain in API GW](./assets/img/AWS_domain_to_APIGW.png)
Add the info from to domain DNS server. Don't forget the . at both ends
![DNS CNAME settings for API GW](./assets/img/domain_to_api_CNAME.png)

## 6) Do some preliminary testing
