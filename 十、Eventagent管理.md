# **十、Eventagent管理** {#eventagent}

**10.1 安装及日志路径**

| Eventagent | 路径 |
| --- | --- |
| 部署路径 | /usr/lib/python2.6/site-packages/eventagent-0.405-py2.6.egg/ |
| 配置文件 | /etc/fit2cloud/userdata.txt |
| 日志文件 | /var/log/eventagent.log (rotate, max 10 files, each size max 1M) |
| 进程 | /usr/bin/python2.7 /usr/bin/eventagent |

**10.2 卸载**

```
f2c-uninstall-agent
```