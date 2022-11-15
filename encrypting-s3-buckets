import boto3

s3 = boto3.client('s3')

aws = s3.list_buckets()

bucket_key = aws['Buckets']

def encrypt_bucket(bucket_name):
    try:
        response = s3.get_bucket_encryption(
            Bucket=bucket_name
        )

    except:
        response = s3.put_bucket_encryption(
            Bucket= bucket_name,
            ServerSideEncryptionConfiguration={
                'Rules': [
                    {
                        'ApplyServerSideEncryptionByDefault': {
                            'SSEAlgorithm': 'aws:kms',
                            'KMSMasterKeyID': 'the arn of your aws key'
                        }
                    },
                ]
            }
        )
        print(bucket_name, "is now encrypted")

for aws_bucket in bucket_key:
    bucket_name = aws_bucket['Name']
    encrypt_bucket(bucket_name)
