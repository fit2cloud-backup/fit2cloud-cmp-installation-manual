## **9.2 RabbitMQ恢复** {#9-2-rabbitmq}

注意事项: 恢复后的虚拟机IP地址不能变

适用于RabbitMQ出问题后无法正常启动的恢复场景

1) 停止fit2cloud服务

| service fit2cloud stop |
| --- |

2) 重建rabbitmq

| bash /opt/f2c-ops/rebuild-rabbitmq.sh |
| --- |

3) 重启scheduler

a. 执行重启命令

| /opt/f2c-ops/f2c-ops.sh -a stop -c webspace-scheduler -v 0.2 |
| --- |

b. 确认RabbitMQ重建成功

*   tailf /var/log/fit2cloud/webspace-scheduler-0.2-console.log  | grep &#039;RabbitMQ check&#039;

直到日志中不再输出带有&#039;RabbitMQ check&#039;

*   登录rabbitmq的控制台，例如[http://192.168.20.180:15671/#/](http://192.168.20.180:15671/#/)，查看overview的queued messages右侧的ready,unacked,total是否均为0(rabbitmq挂了之后，机器的监控数据无法上报，就会堆积，等到恢复后才继续上报。这样的话，在短时间内会有之前的数据上报，所以一直不为0。再次重启rabbitmq的话，队列中的数据就被清空了。数据量不大的话，也不持续增长的话，不清空也没事)，overview的message rates的图是否有曲线波动
*   查看rabbitmq的用户数量是否和fit2cloud的用户数量一致，查看地址例如[http://192.168.20.180:15671/#/users](http://192.168.20.180:15671/#/users)

以上三个条件满足，就表示rabbitmq重建成功

4) 启动fit2cloud

| service fit2cloud start |
| --- |

5) 确认服务恢复

tailf /var/log/fit2cloud/webspace-scheduler-0.2-console.log  | grep &#039;Server connected&#039;

如果有Server connected的日志打印出来，表示rabbitmq与被管理的主机正在建立连接，这个过程需要等待。用admin用户登录例如[http://192.168.20.180/admin/servers](http://192.168.20.180/admin/servers)，可看到所有被管主机的心跳连接状态直到所有的被管主机心跳都恢复正常，表示rabbitmq完全恢复