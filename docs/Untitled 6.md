你这个项目每次重开服务，其实是固定流程，按下面来就行。

一、每次重新开启服务的步骤（Windows）

打开 PowerShell。
进入项目目录：
cd "c:\Users\27203\Desktop\习题库"
启动服务（推荐用虚拟环境里的 Python）：
python.exe -m flask --app app run
看到下面这句就说明启动成功：
Running on http://127.0.0.1:5000
浏览器打开：
http://127.0.0.1:5000/
二、关闭服务

回到运行服务的那个终端。
按 Ctrl+C 停止。

三、如果提示端口被占用（5000 已在使用）

查占用进程：
Get-NetTCPConnection -LocalPort 5000 -State Listen | Select-Object LocalAddress,LocalPort,OwningProcess
结束占用进程（把 PID 换成上一步查到的）：
Stop-Process -Id 进程号 -Force
再执行启动命令。
四、哪些信息会被保存
会保存（持久化到数据库）：

题目内容、答案、更新时间
标签及题目-标签关联
批注（手动/AI）
章节和小节归属
难度值（0-180）
这些数据都在数据库文件里：
question_bank.sqlite3

数据库初始化和字段迁移逻辑在：
db.py