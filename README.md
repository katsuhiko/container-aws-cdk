# AWS CLI

## サーバー起動

```
cd ./
docker-compose up -d
docker exec -it aws-cdk /bin/bash
```

```
# 最初の一回のみ実施（AWS接続情報の設定）
aws configure
```


## コンテナのリビルド（AWS CLIの最新化）

```
docker-compose build --no-cache
```


## AWS Configure 設定例

```
cat ~/.aws/credentials

[default]
aws_access_key_id = <アクセスキーID>
aws_secret_access_key = <シークレットアクセスキー>

[switch-role1]
mfa_serial = arn:aws:iam::<Switch元AWSアカウントID>:mfa/<アカウント>
role_arn = arn:aws:iam::<Switch先AWSアカウントID>:role/<Switch先ロール>
source_profile = default
```

```
cat ~/.aws/config

[default]
region = ap-northeast-1
output = json

[profile switch-role1]
region = ap-northeast-1
output = json
```
