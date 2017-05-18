## **8.2 定时备份配置-使用OSS** {#8-2-oss}

本备份方式为在监控用FIT2CLOUD上配置各个组件的定时备份脚本任务，定时备份脚本任务每日备份时间时在相应主机上运行，将备份文件打包并上传到OSS，并清理多余的备份文件。这种方式需要在各个服务器上事先安装osscmd命令并配置access key, secret key。

| 组件 | 备份脚本离线包路径 |
| --- | --- |
| FIT2CLOUD | 备份脚本: devops/fit2cloud/backup-to-oss.sh |
| JENKINS | 备份脚本: devops/jenkins/backup.sh |
| NEXUS | 备份脚本: devops/nexus/backup-to-oss.sh |
| GITLAB | GitLab为分布式版本控制系统，这一步可暂时不进行配置。 |

备份验证:

首先安装osscmd并配置oss accesskey和secret，之后登录各个服务器执行OSS Command Line查看，执行前把命令中&lt;bucket&gt;替换成实际bucket名字:

| 组件 | 查看命令 |
| --- | --- |
| 查看FIT2CLOUD备份 | osscmd listallobject oss://&lt;bucket&gt;/fit2cloud/ |
| 查看JENKINS备份 | osscmd listallobject oss://&lt;bucket&gt;/Jenkins/ |
| 查看NEXUS私有库备份 | osscmd listallobject oss://&lt;bucket&gt;/fit2cloud-backup/nexus/ |
| 查看Nexus公共库备份 | osscmd listallobject oss://&lt;bucket&gt;//fit2cloud-backup/nexus-public |