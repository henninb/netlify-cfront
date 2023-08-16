Deploy this code to AWS Cloudfront with an S3 Bucket
create an s3 bucket: cfront.bhenning.com
default configuration


create a cloudflare distribution
origin: cfront.bhenning.com.s3.us-east-1.amazonaws.com

create Origin access control settings
redirect HTTP to HTTPS
do not enable security protection (WAF)

{
        "Version": "2008-10-17",
        "Id": "PolicyForCloudFrontPrivateContent",
        "Statement": [
            {
                "Sid": "AllowCloudFrontServicePrincipal",
                "Effect": "Allow",
                "Principal": {
                    "Service": "cloudfront.amazonaws.com"
                },
                "Action": "s3:GetObject",
                "Resource": "arn:aws:s3:::cfront.bhenning.com/*",
                "Condition": {
                    "StringEquals": {
                      "AWS:SourceArn": "arn:aws:cloudfront::423310193800:distribution/E8KGVCVSS8FVD"
                    }
                }
            }
        ]
      }

default root objecct: index.html
wait for the distribution to deploy
d1p4slzwqt8ecr.cloudfront.net

