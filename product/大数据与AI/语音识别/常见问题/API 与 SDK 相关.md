
### 语音识别接口的 HTTP 请求返回鉴权失败？
请用户对照参数表检查自己的参数是否正确上传。如果想快速接入，推荐使用官网提供的 SDK。

###  语音识别服务识别结果报错无效的 URL 地址？
用户提供的 URL 地址需要是公网的 url，能被腾讯云访问。可使用腾讯云提供的 cos 服务存放音频并使用相关的 url。也要请用户排查防火墙是否拦截，是否内网 IP，是否存放于其他服务提供商无法被腾讯云下载等问题。

### 语音识别调用接口服务的时报错"未注册的 AppId"？
用户未注册，用户需要按照语音识别入门开通语音识别服务方可使用服务。
