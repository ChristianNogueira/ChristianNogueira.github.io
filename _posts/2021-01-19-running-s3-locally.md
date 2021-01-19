---
title: "Running S3 Locally"
categories:
  - Blog
tags:
  - AWS
  - S3
---

S3 is a nice tool, but for development, it can be very tricky when it comes to costs.

This is when helps to have an alternative way to host it locally for developing and prototyping.

For this, we can use [Minio](https://min.io/). This is an Open Source project to work as a storage stack. The awesome part is that you can use aws-cli and all other compatible tools to work with Minio with a few changes.

Here will show a way to run it locally and how to configure aws-cli to work with it.

Lunching it in docker can be done with the official image as:

```
$ sudo docker run -d -p 9000:9000 --name=s3 -e MINIO_ACCESS_KEY=access-key -e MINIO_SECRET_KEY=secret-key -v /mnt/data:/data minio/minio server /data
```

Change `access-key` and `secret-key` with a user and password you desire.

After that, you can access the dashboard at `http://localhost:9000/`. In the dashboard, there is not much that can be done.
You can create a bucket from the dashboard or using aws-cli, but first, we need to configure the credentials.

For not messing with a possible default configuration, we can create a new profile named `mini-test`

```
$ aws configure --profile minio-test
AWS Access Key ID [None]: access-key
AWS Secret Access Key [None]: secret-key
Default region name [None]: 
Default output format [None]: json
```

Now we can use minio always providing the alternative endpoint and this profile.

To create a new bucket `bucket-test`

```
$ aws --endpoint-url http://127.0.0.1:9000 s3api create-bucket --bucket bucket-test --profile minio-test
{
    "Location": "/bucket-test"
}
```

Now we can copy a local file `background.svg` to the bucket `bucket-test`

```
$ aws --endpoint-url http://127.0.0.1:9000 s3 cp ./background.svg s3://bucket-test --profile minio-test
```

And check out the file with `ls`

```
$ aws --endpoint-url http://127.0.0.1:9000 s3 ls s3://bucket-test  --profile minio-test
2021-01-19 18:39:59      18111 background.svg
```

To stop the container

```
$ sudo docker container stop s3
```

As we used a bind mount, all data stored in the volume is available at `/mnt/data/` in the hosting machine.

Other alternatives to AWS S3 but as a service with budget in mind are [Linode](https://www.linode.com/?r=9e1f65ae3b4d04d96c0c9b2ffab83dd7b27435d6) and [Wasabi](https://wasabi.com/) 

