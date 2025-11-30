# AI-Book-Cover-Generator
flowchart LR
    User["User / Client"] -->|"HTTP request with prompt"| APIGW["API Gateway<br/>REST API"]
    APIGW -->|"Invoke Lambda"| Lambda["AWS Lambda<br/>Book Cover Handler"]
    Lambda -->|"InvokeModel"| Bedrock["Amazon Bedrock<br/>(Stability Diffusion)"]
    Lambda -->|"PutObject"| S3["Amazon S3<br/>Book Covers Bucket"]
    Lambda -->|"Generate<br/>Pre-signed URL"| S3
    Lambda -->|"Return URL"| APIGW
    APIGW -->|"JSON response with<br/>pre-signed URL"| User
