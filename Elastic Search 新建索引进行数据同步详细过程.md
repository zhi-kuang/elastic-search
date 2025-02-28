# Elastic Search 添加新索引和同步MYSQL数据库

## 一、创建索引

1、pustman中put请求

~~~
es.scholat.com//search/test_course
~~~

![image-20241206145625353](C:\Users\zzs\AppData\Roaming\Typora\typora-user-images\image-20241206145625353.png)

## 二、创建连接器

![image-20241206145902589](C:\Users\zzs\AppData\Roaming\Typora\typora-user-images\image-20241206145902589.png)

1、选择Mysql

2、输入连接器名称（目前设置的名称和索引一样）

3、将连接器和索引进行关联

![image-20241206150046176](C:\Users\zzs\AppData\Roaming\Typora\typora-user-images\image-20241206150046176.png)

4、生成API key（类似下面这种）

~~~
R2ZURm1wTUI5YzVKZ08tY2RSTzU6TkRqbXgtSWZRYmU4VWo2bzhGeDYxZw==
~~~

5、来到ES部署服务器中添加上刚刚生成的API Key

![image-20241206150543061](C:\Users\zzs\AppData\Roaming\Typora\typora-user-images\image-20241206150543061.png)

6、重启连接器服务

在./elasticsearch文件夹下输入一下命令

~~~
先关闭服务
docker-compose -f ./connectors/connector.yaml down  
再重启服务
docker-compose -f ./connectors/connector.yaml up -d
~~~

7、回到kibana控制台设置数据库服务

![image-20241206151912191](C:\Users\zzs\AppData\Roaming\Typora\typora-user-images\image-20241206151912191.png)

8、点击同步按钮开始同步，看看是否有问题

至此ES服务器端已全部完成