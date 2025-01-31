## 创建实例
1. 登录 [CKafka 控制台](https://console.cloud.tencent.com/ckafka) 。
2. 在 CKafka 实例列表页，单击【新建】。
3. 在 CKafka 实例购买页，选择购买信息。
	- 计费模式：包年包月
	- 地域：选择物理分区相近的地域
	- 可用区：选择可购买的分区
	- 产品规格：根据峰值带宽和磁盘容量选择对应的型号
	- 消息保留：以分钟为单位，最短保留1分钟，最长保留30天
	>?设置了消息保留时间后，过期的消息就会被删除，而删除机制是按照 Ckafka 的分片批量删除的，不是立刻删除的，目前分片的大小是1G，如果分片不到1G 就不会删除。因此，如果您设置的保留时间是1分钟，而分片的数据大小在1分钟内无法增到1G，那么这个时间是无效的，建议延长保留时间，具体根据数据的堆积速度而定。
	- 购买数量：范围在1 - 20个
	- 购买时长：可设置到期后按月自动续费
4. 单击【立即购买】。


## 创建 Topic
1. 在 CKafka 实例列表页，单击目标实例的“ID/名称”，进入实例详情页。
2. 在实例详情页，单击页面顶部的【Topic 管理】。
3. 在 Topic 管理页，单击【新建】按钮。
4. 在编辑 Topic 窗口中，选择分区数和副本数等信息。
 - 名称：Topic 名称，输入后无法更改。
 - 分区数：一个物理上分区的概念，一个 Topic 可以包含一个或者多个 partition，CKafka 以 partition 作为分配单位。
 - 副本数：partition 的副本个数，用于保障 partition 的高可用，为保障数据可靠性，当前不支持创建单副本 Topic，默认开启2副本。
 - 白名单： 开启白名单后，只有白名单中的 IP 才可访问该 Topic，有效保证数据安全（在新建 Topic 和编辑 Topic 页面均可以开启白名单）。
5. 单击【提交】。

>?副本数也算分区个数的，例如客户创建了1个 Topic、6个分区、2个副本，那么分区额度一共用了1 \* 6 \* 2 = 12个。
如果超过了购买的最大分区个数，单击【提交】时会有如下提示：
![](https://main.qcloudimg.com/raw/eeb3b9aa16ef7b5ae6370d56affed865.png)

## 查看实例
1. 在 CKafka 实例列表页，单击目标实例的“ID/名称”，进入实例详情页。
2. 在实例详情页，单击【基本信息】标签页，可查看实例的配置信息、接入方式、消息保留和自动创建 Topic。
如果您开启了自动创建 Topic，将会在服务器上启用主题的自动创建，使用或获取不存在的主题元数据时，将自动使用配置的副本数和分区数进行创建。您可以在【Topic 管理】中查看自动创建的 Topic。
>?
>- 自动创建的 Topic，总数量会根据实例的不同规格有不同的限制。详情请参见 [计费说明](https://cloud.tencent.com/document/product/597/11745)。
>- 【基本信息】中内网 IP 与端口（例如`10.6.206.110:9092`），表示用于获取后端服务的通讯地址，真实访问地址中端口可能存在多个，如果您的服务器配置了访问限制，请在服务器上放通9092后的所有端口。


## 查看 Topic
1. 在 CKafka 实例列表页，单击目标实例的“ID/名称”，进入实例详情页。
2. 在实例详情页，单击【Topic 管理】标签页，可查看 Topic 的监控、分区数、白名单等信息。
