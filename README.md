# AI-Book-Cover-Generator
```mermaid
flowchart LR
    User[User / Client] --> |HTTP request with prompt| APIGW[API Gateway\nREST API]
    APIGW --> |Invoke Lambda| Lambda[AWS Lambda\nBook Cover Handler]
    Lambda --> |InvokeModel| Bedrock[Amazon Bedrock\n(Stability Diffusion)]
    Lambda --> |PutObject| S3[Amazon S3\nBook Covers Bucket]
    Lambda --> |Generate\nPre-signed URL| S3
    Lambda --> |Return URL| APIGW
    APIGW --> |JSON response with\npre-signed URL| User
