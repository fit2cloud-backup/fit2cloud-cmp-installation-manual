## **8.3 定时备份配置-使用SFTP文件存储** {#8-3-sftp}

首先配置SSH拷贝文件不需要key

| 组件 | 备份脚本离线包路径 |
| --- | --- |
| FIT2CLOUD | 备份脚本: devops/fit2cloud/backup-to-sftp.sh |
| JENKINS | 备份脚本: devops/jenkins/backup.sh |
| NEXUS | 备份脚本: devops/nexus/backup-to-sftp.sh |
| GITLAB | GitLab为分布式版本控制系统，这一步可暂时不进行配置。 |