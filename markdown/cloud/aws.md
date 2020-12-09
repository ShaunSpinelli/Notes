# AWS

## S3 (Simple Storage Service)

### Setting up dev s3 service with [moto](https://github.com/spulec/moto)

Starting a mock s3 server, basically acts like s3. In `bash` run

```bash
moto_server s3
```

Then when when creating a client set `endpoint_url` to what the server is running on.

```python
# python example
import boto

client = boto3.client("s3", endpoint_url="http://127.0.0.1:5000/")
```


