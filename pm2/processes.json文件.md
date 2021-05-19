```js
{
  "apps": [
    {
      "name": "deepChart",					     //应用程序名称
      "cwd": "./",								//应用程序所在目录
      "script": "server.js",					 //应用程序脚本
      "log_date_format": "YYYY-MM-DD HH:mm Z",		//日期时间格式化
      "error_file": "./log/node-app.stderr.log",	//自定义应用程序错误日志
      "out_file": "./log/node-app.stdout.log",		//自定义应用程序的日志文件
      "pid_file": "./log/node-geo-api.pid",			//自定义应用程序的pid文件
      "instances": 2,							//启动实例个数
      "min_uptime": "200s",                       //最小运行时间，小于该时间内退出，pm2会认为程序异常退出，此时触发重启max_restarts设置数量
      "max_restarts": 10,						//设置应用程序异常退出重启的次数，默认15次
      "max_memory_restart": "1M",				
      "cron_restart": "1 0 * * *",				//定时重启
      "watch": false,							//是否启用监控模式
      "merge_logs": true,						
      "exec_interpreter": "node",				//应用程序脚本类型，默认为node
      "exec_mode": "cluster",					//默认启动模式 cluster（集群），默认fork
      "autorestart": false,						//启用或禁用程序崩溃或退出自动重启
      "vizion": false							//版本控制
    }
  ]
}


pm2 start processes.json
```

