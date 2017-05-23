## **9.3 JENKINS恢复** {#9-3-jenkins}

恢复Jenkins所有设置和每个Job的构建历史

注意事项: 恢复后的虚拟机IP地址不能变

1.  下载jenkins-all-in-one.zip包
2.  一键安装Jenkins
3.  恢复构建任务

把ThinBakcup插件备份出来的最新的文件，文件名类似FULL-2016-07-05_12-35.zip放到/opt/fit2cloud/jenkins/backup目录下，并解压

1.  恢复插件

把备份文件中plugins.tar压缩包解压后的插件全部copy到/opt/apache-tomcat-7.0.65/jenkins/plugins目录下

1.  重启tomcat后 ，进入[http://&lt;Jenkins IP&gt;/thinBackup/backupsettings](http://11.8.36.90/thinBackup/backupsettings)

Backup directory这一项的内容填/opt/fit2cloud/jenkins/backup

保存后 ，进入[http://](http://11.8.36.90/thinBackup/restoreOptions)[&lt;Jenkins IP&gt;](http://11.8.36.90/thinBackup/backupsettings)[/thinBackup/restoreOptions](http://11.8.36.90/thinBackup/restoreOptions)

选择好要恢复的版本，点击restore

1.  最后再重启tomcat ，这样jenkins所有设置和每个job的build历史都可以正常恢复了。

7) 恢复Maven settings

拷贝备份文件中的settings.xml到要恢复的机器的/root/.m2/目录下