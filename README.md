# aws-cfn-s3_via_apigw
Cloudformation templates to create a service that can upload and download files on S3 via API gateway and create a custom domainname for the API.

It uses the [S3viaAPIGW template](./S3viaAPIGW.md) to create the API gateway. <BR><BR>
If you want the API Gateway to be accesable via your own domain name use the [CustomDomain template](./CustomDomain.md) to create a verified custom domain <BR>
ANd link the API Gateway to CustomDomain.
