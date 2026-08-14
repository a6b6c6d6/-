# 水贴专用（Linux.sb AI 回帖助手）

一款给 [linux.sb](https://linux.sb/)（烧饼社区）准备的 **Tampermonkey 油猴脚本**：在帖子页注入「水贴专用」悬浮按钮，抓取帖子内容、调用你自己配置的 AI 接口生成回复，再一键填入回复编辑器。

> 脚本只做「抓取 + 调用你自配的 AI + 回填」，**不内置任何 API 密钥**，配置全部存在本地浏览器，密钥不会上传或写入日志。

## 功能特性

- **三种抓取范围**：`仅首楼` / `楼主全部发言` / `全帖内容`
- **两种请求格式**：`Responses`（/responses）与 `Chat Completions`（/chat/completions）
- 抓取内容自动清洗为 Markdown：段落、列表、代码块、引用（`>`）保留，图片/头像/签名等无关元素剔除，可带发言人标识
- 回复生成后可在面板内**手动修改**，再一键填入编辑器
- 面板可拖动、可折叠设置区，错误信息中文提示

## 安装

1. 安装脚本管理器 [Tampermonkey](https://www.tampermonkey.net/)（Edge / Chrome 均可）
2. 打开本仓库的 `linux.sb-ai-reply.user.js`，点右上角 **Raw** 按钮，Tampermonkey 会自动识别并弹出安装窗口
3. 确认安装即可

> 也可直接访问 raw 链接安装：`https://raw.githubusercontent.com/<你的用户名>/<仓库名>/main/linux.sb-ai-reply.user.js`

## 配置

打开任意帖子页（如 `https://linux.sb/topic/11236`），点右下角「水贴专用」→ 展开「设置」，填入：

| 配置项 | 说明 | 示例 |
| --- | --- | --- |
| baseUrl | API 地址 | https://api.openai.com/v1 |
| apiKey | 密钥 | sk-xxxx |
| model | 模型名 | gpt-4.1-mini |
| apiFormat | 请求格式 | responses / chat |

其余项（温度、最大 tokens、最大抓取字符数、系统提示词、发言人标识）都有默认值，可按需调整。

## 使用

1. 打开帖子页，点右下角「水贴专用」
2. 选抓取范围，点「抓取并生成回复」
3. 在预览框里修改满意后，点「填入编辑器」
4. 点论坛的「回复」按钮发布

> 注意：`填入编辑器` 需要你**已登录 linux.sb**，否则页面只有「登录后回复」，没有回复框。

## 截图

<!-- 发布前替换为你的脚本界面截图 -->
![界面截图](https://example.com/a.jpg)

## 关于 `@connect *`

脚本元数据里 `@connect` 用了通配符 `*`，是为了兼容任意自建/第三方 AI 网关。若你只在固定域名调用，可把它改成具体域名（如 `@connect api.openai.com`）以收紧跨域权限。

## 许可证

[MIT](LICENSE)
