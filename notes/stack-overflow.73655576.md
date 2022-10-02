---
id: ninqc6d8e9iwybhy5y5ci4d
title: 'Upload image to S3 from memory'
desc: 'Convert Pandas Dataframe to Image and Upload Directly to S3 Bucket Without Saving Locally Using Python'
updated: 1664736840113
created: 1662690420000
tags:
  - python
  - s3
  - pandas
  - dataframe
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73655576/6456163) for the original answer.

I created [an issue](https://github.com/dexplo/dataframe_image/issues/43) on the `dataframe_image` repository asking this question to the library author, and below is my implementation of his suggestion:

```python
import boto3
import dataframe_image as dfi
from io import BytesIO

# create the buffer in which to store the generated image
png_io = BytesIO()

# assuming that your dataframe is stored as `df` variable
df.dfi.export(png_io)

# create the boto3 client and upload the BytesIO directly;
# create your client in whatever way works for you
session = boto3.session.Session(aws_access_key_id=aws_access_key_id, aws_secret_access_key=aws_secret_access_key, region_name=region_name)
s3_client = session.client('s3')
s3_client.upload_fileobj(png_io, 'your_destination_folder/your_destination_file')
```

For more information, check this [TechOverflow post](https://techoverflow.net/2021/03/08/how-to-use-boto3-to-upload-bytesio-to-wasabi-s3-in-python/) and this [StackOverflow post](https://stackoverflow.com/a/69443870/6456163).

