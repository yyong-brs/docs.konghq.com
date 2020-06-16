| 主题          | 跳过阅读时间 |
| ------------- | ------------ |
| 5分钟快速开始 | true         |

**开始之前：**确认你已经安装了Kong--只需要花费1分钟!

在本节中，你将学习如何去管理你的kong实例。首先，我们让你启动kong，以便让你访问到Restful管理接口，通过该接口可以管理你的服务、路由、消费者等。通过管理API发送的数据存储在kong的数据存储中（kong支持postgresql和Cassandra）。

1. ####  启动 Kong

   ------

   通过运行以下的kong migrations命令来准备你的数据存储：

   ```shell
   $ kong migrations bootstrap [-c /path/to/kong.conf]
   ```

   你应该会看到消息输出告诉你 kong已经成功初始化你的数据库。如果没有，你可能在你的配置文件中配置了错误了数据库连接信息。

   现在让我们来启动kong:

   ```shell
   $ kong start [-c /path/to/kong.conf]
   ```

   **提示：**命令行接收你指定自己的配置文件选项(-c /path/to/kong.conf)

2. ####  验证kong已经成功启动

   ------

   如果一切正常，你应该看到消息（kong started）提醒你kong正在运行。

   默认情况下，kong监听以下端口：

   - `:8000` 用来监听客户端的http请求，然后转发到你的上游服务（upstream services）。
   - `:8443` 用来监听客户但的https请求，这个端口和`:8000` 端口拥有类似的功能行为，除了https的差别。这个端口可以通过配置文件设置来禁用。
   - `:8001` 用来配置Admin API的监听端口。
   - `:8444` 监听Admin API https的请求

3. ####  停止Kong

   ------

   如果需要，你可以通过一下命令来停止Kong 进程：

   ```shell
   $ kong stop
   ```

   

4. #### 重新加载kong

   通过以下命令来实现不停机重新加载kong:

   ```shell
   $ kong reload
   ```

   

#### 后续步骤

------

现在你已经运行了kong,你可以通过Admin Api和kong进行交互。

首先，请转到 配置服务（TODO:引用）
