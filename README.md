# BlogBeacon_Stream

# Blog Generator using AWS Bedrock and AWS Lambda

This is a backend serverless project that generates a 200-word blog on any given topic using Amazon Bedrock's LLaMA3 model. The generated content is saved to an Amazon S3 bucket.

## Technologies Used

- Amazon Bedrock (LLaMA3 model)
- AWS Lambda (Python)
- Amazon S3
- boto3 (Python SDK for AWS)
- API Gateway (optional, for HTTP triggers)

## Project Structure


## How It Works

1. A topic is passed to the Lambda function via an event (can be triggered manually or via API Gateway).
2. The function uses Amazon Bedrock to generate a blog post using the Meta LLaMA3 model.
3. The blog content is saved to an Amazon S3 bucket under the path `blog-output/{timestamp}.txt`.

## Setup Instructions

### IAM Role Requirements

Ensure the Lambda function's execution role has the following permissions:
- `bedrock:InvokeModel`
- `s3:PutObject`

### Lambda Deployment

1. Go to the AWS Lambda Console.
2. Create a new function using Python 3.10 or higher.
3. Paste the code from `lambda_function.py` into the function editor.
4. Make sure your region is set to `ap-south-1`.
5. Specify your S3 bucket name in the code (`awsbedrockproject01`, or update to your own).
6. (Optional) Set up an API Gateway to call the function with a POST request.

### Example API Gateway Input

If using API Gateway to trigger the Lambda, send a JSON payload like this:

```json
{
  "blog_topic": "Impact of Climate Change"
}
{
  "body": "{\"blog_topic\": \"Future of Artificial Intelligence\"}"
}
blog-output/143255.txt
