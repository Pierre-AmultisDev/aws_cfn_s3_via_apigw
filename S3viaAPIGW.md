# S3 via API Gateway creation
S3viaAPIGW is used to create access to a S3 bucket via API gateway without Lmabda function
It uses several independent submodules and Cloudformation templates.
<BR>
__Steps for the S3viaAPIGW template__:
 
## 1) Create basic structure in root folder (so one folder up)
AWS CloudFormation Stack files for the solution
```
cd ..
```

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

## 2) Set files for this project in root folder
```
_AWS-region.txt      AWS region where to create stack
_AWS-profile.txt     AWS profile name used to create stack 
_AWS_costcenter.txt  costcenter tag to use when stack is created 
```

## 3) Update stack_template file
Replace parametervalues in S3viaAPIGWv*-boiler.json 
```
BucketName: Name of the S3 bucket to create
ApiName:    Name for the API gateway 

```
## 4) Create the API Gateway stack using the Cloudformation script
Update the content of _current_version with the this template (for example S3viaAPIGWv001) and run the required command in ../stack_scripts/yaml

## 5) Preliminary testing
Uploading files:
```
curl -X PUT \
  https://your-api-endpoint.execute-api.region.amazonaws.com/prod/files/document.pdf \
  -H 'x-api-key: your-api-key-here' \
  -H 'Content-Type: application/pdf' \
  --data-binary '@/path/to/your/document.pdf'
```
Downloading files:
```
curl -X GET \
  https://your-api-endpoint.execute-api.region.amazonaws.com/prod/files/document.pdf \
  -H 'x-api-key: your-api-key-here' \
  --output downloaded-document.pdf
```