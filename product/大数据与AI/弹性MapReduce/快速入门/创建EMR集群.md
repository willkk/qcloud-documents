## 操作场景
本文为您介绍通过 EMR 控制台创建一个 EMR 集群的操作。

## 操作步骤
登录 [EMR 控制台](https://console.cloud.tencent.com/emr)，在集群列表页单击【创建集群】。

### 1. 可用区与软件配置
- **计费模式**：支持包年包月和按量计费。
 - 包年包月：提前预付 N 个月的产品费用，相比按量付费价格更低。
 - 按量计费：按照使用时长付费，需对账户进行实名认证，在开通时需冻结1小时的费用（代金券不可用作冻结凭证），销毁时退还。
- **地域和可用区**：目前支持的地域有：广州、上海、北京、新加坡、硅谷、成都、孟买。不同地域的云产品之间内网不互通。
- **版本和组件**：EMR 推荐了一些常用的 Hadoop 软件搭配，您也可以根据自身需求组合各软件。
-  **[Kerberos 安全集群](https://cloud.tencent.com/document/product/589/35064)**：是否开启集群的 Kerberos 认证功能。一般的个人用户集群无需该功能，默认关闭。
-  **访问外部集群**：配置外部集群 HDFS 的访问地址信息后，可以读写外部集群的数据。
![](https://main.qcloudimg.com/raw/06b5ed9c4a021da5a13d534370117e5a.png)


### 2. 硬件配置
- **节点高可用（HA）**：选择【启动高可用】后，将会默认开启2个 Master 节点，至少3个 Core 节点，以及3个 Common 节点，节点类型介绍请参见 [节点类型说明](https://cloud.tencent.com/document/product/589/14624)。
- **硬件配置**：节点规格配置，EMR 提供了多种节点规格，您可以根据业务需要自由选择节点类型、核数、内存、磁盘类型及大小。
>?目前仅 Core 节点支持挂载多种云盘类型（每种云盘类型最多只能选择1次）和多块云盘（最多5块）。

- **集群网络**：为保证 EMR 集群的安全性，我们将集群各节点放入了一个私有网络中，您需要设置一个私有网络以保证 EMR 集群的正确创建。
![](https://main.qcloudimg.com/raw/01e6a3d1d446db04a96c1f43aa960dfd.png)
Core节点支持挂载多云盘
![](https://main.qcloudimg.com/raw/a6082dbe259f3b1aa18d597b1a9bd203.png)

### 3. 基础配置
- **集群名称**：通过设置集群名称，来区分不同的 EMR 集群。
- **安全组**：安全组具有防火墙功能，用于设置云服务器 CVM 的网络访问控制。如果没有安全组，用户可以输入新的安全组名称新建一个安全组。若已经有在使用的安全组可以直接选择使用。
 - 创建安全组：EMR 帮助用户创建一个安全组，开启22和30001端口及必要的内网通信网段。
 - 已有 EMR 安全组：选择已创建的 EMR 安全组作为当前实例的安全组，开启22和30001端口及必要的内网通信网段。
- **对象存储**：开启对象存储（COS）后，EMR 集群可以直接计算存储在 COS 中的数据，以实现计算存储分离，降低大数据处理成本。为保证 EMR 有权限访问到 COS 中的数据，请输入 COS 的 API 密钥。
- **添加引导操作**：引导脚本操作方便您在生产集群的过程中执行自定义脚本，以便您修改集群环境、安装第三方软件和使用自有数据。
![](https://main.qcloudimg.com/raw/7a5093615f5fbbf46352b2161f7f7662.png)


### 4. 完成创建
完成以上配置后，单击【购买】进行支付，支付成功后 EMR 集群进入创建过程，在大约10分钟后即可在 EMR 控制台中找到刚创建的集群。
>!您可以在 CVM 控制台中查看各节点的实例信息，为保证 EMR 集群的正常运行，请不要在 CVM 控制台中更改这些实例的配置信息。
