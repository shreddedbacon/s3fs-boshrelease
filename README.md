# s3fs bosh release

A BOSH release to make use of s3fs.

### Notes
* [s3fs](https://github.com/s3fs-fuse/s3fs-fuse)
* Can't mkdir in minio with s3fs: https://github.com/minio/minio/pull/4426

### Usage
```
chmod 600 /var/vcap/jobs/s3fs/etc/password

mkdir -p /var/vcap/store/bucket/

minio="-o url=http://10.244.0.22:9001/"
endpoint="-o endpoint=us-east-1"
bucket=test
mountpath=/var/vcap/store/bucket/
options="-o allow_other,use_path_request_style"

/var/vcap/packages/s3fs/bin/s3fs $bucket $mountpath -o passwd_file=/var/vcap/jobs/s3fs/etc/password $minio $endpoint $options
```
