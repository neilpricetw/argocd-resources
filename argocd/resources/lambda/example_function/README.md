# Example Lambda Function to Upload to S3

## Quick Deployment Steps

- Zip it: zip hello-world.zip index.mjs
- Upload: aws s3 cp hello-world.zip s3://your-source-bucket-name/
