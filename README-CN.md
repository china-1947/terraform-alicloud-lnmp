terraform-alicloud-lnmp
=====================================================================

本 Terraform 模块将基于阿里云 ECS 实例来部署 lnmp(Linux+Nginx+MySQL+PHP)。

## Terraform 版本

本模板要求使用版本 Terraform 0.12 和 阿里云 Provider 1.56.0+。

## 用法

```hcl
module "lnmp"  {
  source  = "terraform-alicloud-modules/lnmp/alicloud"
  region                     = "cn-beijing"                
  profile                    = "Your-TF-Profile"
  
  instance_name              = "myLNMP"
  instance_password          = "YourPassword123"
  instance_type              = "ecs.c5.large"
  system_disk_category       = "cloud_efficiency"
  security_group_ids         = ["sg-12345678"]
  vswitch_id                 = "vsw-fhuqiexxxxxxxxxxxx"
  internet_max_bandwidth_out = 50

  db_name          = "YourdbName"
  db_user          = "YourAccountName"
  db_password      = "YourdbPassword"
  db_root_password = "YourPassword"
}
```

## 示例

* [在 ECS 上部署 lnmp 示例](https://github.com/terraform-alicloud-modules/terraform-alicloud-lnmp/tree/master/examples/complete)

## 注意事项

* 本 Module 使用的 AccessKey 和 SecretKey 可以直接从 `profile` 和 `shared_credentials_file` 中获取。如果未设置，可通过下载安装 [aliyun-cli](https://github.com/aliyun/aliyun-cli#installation) 后进行配置。

提交问题
------
如果在使用该 Terraform Module 的过程中有任何问题，可以直接创建一个 [Provider Issue](https://github.com/terraform-providers/terraform-provider-alicloud/issues/new)，我们将根据问题描述提供解决方案。

**注意:** 不建议在该 Module 仓库中直接提交 Issue。

作者
-------
Created and maintained by Alibaba Cloud Terraform Team(terraform@alibabacloud.com)

许可
----
Apache 2 Licensed. See LICENSE for full details.

参考
---------
* [Terraform-Provider-Alicloud Github](https://github.com/terraform-providers/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://www.terraform.io/docs/providers/alicloud/index.html)
