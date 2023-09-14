# midjourney-proxy

代理 MidJourney 的discord频道，实现api形式调用AI绘图

## 主要功能
- [x] 支持 Imagine 指令和相关动作
- [x] Imagine 时支持添加图片base64，作为垫图
- [x] 支持 Blend(图片混合)、Describe(图生文) 指令
- [x] 支持任务实时进度
- [x] 支持中英文翻译，需配置百度翻译或gpt
- [x] prompt 敏感词判断，支持覆盖调整
- [x] user-token 连接 wss，可以获取错误信息和完整功能
- [x] 支持 discord域名(server、cdn、wss)反代，配置 mj.ng-discord
- [x] 支持多账号配置，每个账号可设置对应的任务队列

**🚀 更多功能请查看 [midjourney-proxy-plus](https://github.com/litter-coder/midjourney-proxy-plus)**
> - [x] 支持开源版的所有功能
> - [x] 支持 Shorten(prompt分析) 指令
> - [x] 支持焦点移动: Pan ⬅️ ➡️ ⬆️ ⬇️
> - [x] 支持图片变焦: Zoom 🔍
> - [x] 支持局部重绘: Vary (Region) 🖌
> - [x] 支持几乎所有的关联按钮动作和🎛️ Remix模式
> - [x] 支持获取图片的seed值
> - [x] 中英文翻译额外支持deepl
> - [x] 账号池持久化，动态维护
> - [x] 支持获取账号/info、/settings信息
> - [x] 内嵌管理后台页面

## 使用前提
1. 注册并订阅 MidJourney，创建自己的频道，参考 https://docs.midjourney.com/docs/quick-start
2. 获取用户Token、服务器ID、频道ID：[获取方式](./docs/discord-params.md)

## 快速启动
1. `Railway`: 基于Railway平台，不需要自己的服务器: [部署方式](./docs/railway-start.md)；若Railway不能使用，可使用Zeabur启动
2. `Zeabur`: 基于Zeabur平台，不需要自己的服务器: [部署方式](./docs/zeabur-start.md)
3. `Docker`: 在服务器或本地使用Docker启动: [部署方式](./docs/docker-start.md)

## 本地开发
- 依赖java17和maven
- 更改配置项: 修改src/main/application.yml
- 项目运行: 启动ProxyApplication的main函数
- 更改代码后，构建镜像: Dockerfile取消VOLUME的注释，执行 `docker build . -t midjourney-proxy`

## 配置项
- mj.accounts: 参考 [账号池配置](./docs/config.md#%E8%B4%A6%E5%8F%B7%E6%B1%A0%E9%85%8D%E7%BD%AE%E5%8F%82%E8%80%83)
- mj.task-store.type: 任务存储方式，默认in_memory(内存\重启后丢失)，可选redis
- mj.task-store.timeout: 任务存储过期时间，过期后删除，默认30天
- mj.api-secret: 接口密钥，为空不启用鉴权；调用接口时需要加请求头 mj-api-secret
- mj.translate-way: 中文prompt翻译成英文的方式，可选null(默认)、baidu、gpt、deepl
- 更多配置查看 [配置项](./docs/config.md)

## 相关文档
1. [API接口说明](./docs/api.md)
2. [版本更新记录](https://github.com/novicezk/midjourney-proxy/wiki/%E6%9B%B4%E6%96%B0%E8%AE%B0%E5%BD%95)

## 注意事项
1. 作图频繁等行为，可能会触发midjourney账号警告，请谨慎使用
2. 常见问题及解决办法见 [Wiki / FAQ](https://github.com/novicezk/midjourney-proxy/wiki/FAQ)
3. 在 [Issues](https://github.com/novicezk/midjourney-proxy/issues) 中提出其他问题或建议
4. 感兴趣的朋友也欢迎加入交流群讨论一下，扫码进群名额已满，加管理员微信邀请进群

 <img src="https://raw.githubusercontent.com/novicezk/midjourney-proxy/main/docs/manager-qrcode.png" width="220" alt="微信二维码"/>

## 应用项目
依赖此项目且开源的，欢迎联系作者，加到此处展示
- [wechat-midjourney](https://github.com/novicezk/wechat-midjourney) : 代理微信客户端，接入MidJourney，仅示例应用场景，不再更新
- [stable-diffusion-mobileui](https://github.com/yuanyuekeji/stable-diffusion-mobileui) : SDUI，基于本接口和SD，可一键打包生成H5和小程序
- [ChatGPT-Midjourney](https://github.com/Licoy/ChatGPT-Midjourney) : 一键拥有你自己的 ChatGPT+Midjourney 网页服务
- [MidJourney-Web](https://github.com/ConnectAI-E/MidJourney-Web) : 🍎 Supercharged Experience For MidJourney On Web UI
