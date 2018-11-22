### math库

`import math`

`dir(math)`

`help(math.pow)`

### os库

`import os`

##### 得到当前的工作目录

`os.getcwd()`

##### 改变工作目录

`path='c:\\test'`

`os.chdir(path)`

##### 对文件重命名

`os.rename('test.txt','test1.txt')`

##### 删除文件

`os.remove('test1.txt')`

### random库

`import random`

在list中随机选择

`random.choice(['C++','Java','python'])`

生成1到100之间的随机整数

`random.randint(1,100)`

生成0到1之间的随机浮点数

`random.random()`

生成5到10之间的随机浮点数

`random.uniform(5,10)`

生成list中随机的n个选择

`random.sample(range(100),10)`

`random.sample(['a','b','v','d','r'],3)`

将list中的元素顺序打乱

`s=['a','b','v','d','r']`

`random.shuffle(s)`

### datetime库

`import datetime`

##### 日期类

`form datetime import date`

获取今天日期

`date.today()`

##### 时间类

创建时间

`from datetiem import time`

`tm= time(23,20,35)`

`print(tm)`

##### datetime类

`from datetime import datetime` 

`dt=datetime.now()`

将时间转化为固定格式

`dt.strftime('%a, %b %d %Y %H:%M')`

将本地时间转为时间蹉

`ds=dt.timestamp()`

将时间蹉转化为本地时间

`dt_=datetime.fromtimestamp(ts)`

