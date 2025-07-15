# aws-cfn-s3_via_apigw
Cloudformation template to create a service that can upload and download files on S3 via API gateway

Replace parametervalues in *-boiler.json 
```
BucketName: Name of the S3 bucket to create
ApiName:    Name for the API gateway 

```

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