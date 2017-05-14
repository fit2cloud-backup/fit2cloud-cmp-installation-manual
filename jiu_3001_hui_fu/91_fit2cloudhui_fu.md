## **9.1 FIT2CLOUD恢复** {#9-1-fit2cloud}

注意事项: 恢复的FIT2CLOUD服务器IP地址不能变，除非安装之初就使用域名

1.  重新下载FIT2CLOUD最新安装包

参照前面安装包下载地址下载

1.  安装FIT2CLOUD

同前面安装步骤

1.  停止FIT2CLOUD

| service fit2cloud stop |
| --- |

1.  下载备份配置文件并替换

运行前先替换命令中&lt;bucket&gt;

| cd /opt/fit2cloud |
| --- |

1.  重新启动FIT2CLOUD

| service fit2cloud restart |
| --- |

1.  登录验证

浏览器输入登录: http://&lt;FIT2CLOUD_IP&gt;