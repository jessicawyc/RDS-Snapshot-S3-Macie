# RDS-Snapshot-S3-Macie
from 2020 Jan AWS support this new function, so we can use this easy way to export rds into S3 in parque format, then use macie to discover the sensitive data
## Step1 建立一个导出任务
输入参数信息,建议可以在平台中先手动操作一次,然后相关参数会

```
region='eu-west-3'
taskname='test0512'
ssarn="arn:aws:rds:eu-west-3:<accoundid>4:snapshot:export2s3test"
myexportbucket="dcp-macie-eu-west-3"
iamrole="arn:aws:iam::<accoundid>:role/service-role/rds-snapshot-s3-role"
mykey="arn:aws:kms:eu-west-3:<accoundid>:key/<keyid>"
```
运行以下命令行创建导出任务,然后去喝杯🍵
```
aws rds start-export-task \
    --export-task-identifier $taskname\
    --source-arn $ssarn \
    --s3-bucket-name $myexportbucket\
    --iam-role-arn $iamrole\
    --kms-key-id $mykey\
    --region=$region

```
同时运行的最大任务数量为5个
