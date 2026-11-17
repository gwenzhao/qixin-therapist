# 栖心 · 七幕 · 一条线

一个**本地优先、用户自带 API Key** 的自我探索与情绪书写工具。

七幕路径：**看见 → 溯源 → 哀悼 → 接纳 → 重构 → 绽放 → 新生**。  
每一幕分为「三层深入 + 一次收束」，再把收束句带入下一幕。

> 栖心不是心理治疗，也不是医疗设备。它不能替代专业心理咨询、诊断或危机干预。  
> 如果你或你身边的人正处于危险中，请优先联系现实中的人和急救资源。

![栖心首页预览](preview.png)

## 这是什么

- 一个可以慢慢写完的自我探索页面，而不是开放式聊天机器人
- 每一幕都有明确的深度、终点和跨幕传递
- AI 只负责写「注脚」和润色，不控制流程、不追问
- 默认使用本地注脚；连接 DeepSeek 后才启用 AI 文字
- 所有记录保存在浏览器 `localStorage`，不经过项目作者的服务器
- 可导出 Markdown 档案和 JSON 备份

## 不是什么

- 不是心理治疗、诊断工具或医疗设备
- 不是危机干预服务
- 不保证 AI 输出正确、适用或无害
- 不适合 18 岁以下用户单独使用
- 不适合在公共电脑上保存私密记录

完整边界见网页版 [隐私与使用边界](legal.html)，或仓库中的 [DISCLAIMER.md](DISCLAIMER.md)、[PRIVACY.md](PRIVACY.md)。

## 快速开始

### 方式一：直接打开

下载 `index.html`，用 Chrome、Edge 或 Safari 打开即可。  
页面不依赖构建工具，也没有外部脚本。

### 方式二：GitHub Pages

1. 新建一个 GitHub 仓库
2. 把本目录的文件放到仓库根目录（`index.html` 必须在根目录）
3. 仓库 **Settings → Pages**
4. **Source** 选择 `Deploy from a branch`
5. 分支选择 `main`，目录选择 `/ (root)`
6. 保存后等待 GitHub Pages 生成地址
7. 在生成的 `https://<用户名>.github.io/<仓库名>/` 地址上测试「设置 → 测试连接」

> 建议仓库名使用英文和连字符，例如 `qixin-therapist`，不要使用空格。  
> 更完整的命令与上线检查见 [DEPLOY.md](DEPLOY.md)。

## 连接 DeepSeek（可选）

1. 在 [DeepSeek 开放平台](https://platform.deepseek.com/api_keys) 创建自己的 API Key
2. 打开页面右上角「设置与数据」
3. 填入 Key，点击「测试连接」
4. 连接成功后，每一层记录会发送给 DeepSeek 生成注脚

说明：

- 项目**不包含任何 API Key**
- Key 默认只放在 `sessionStorage`；勾选「记住」后才放入 `localStorage`
- API 地址固定在 `https://api.deepseek.com`，页面不提供自定义网关
- API 费用由用户自己的 Key 承担
- 不连接 API 时仍可使用本地模式完成七幕

## 数据与隐私

- 记录保存在当前浏览器的 `localStorage`，键名 `qixin.therapist.v1.state`
- 本地记录**没有加密**，同一浏览器中的扩展或其他脚本理论上可以读取
- 连接 DeepSeek 时，当前层的记录和本次主线摘要会发送给 DeepSeek
- 不包含统计工具、广告、第三方字体或 CDN
- 设置里可以导出、清空数据；导出 JSON 不包含 API Key
- 设置里提供「清除浏览器中的 Key」，也会清理旧版本遗留的 Key 名称
- 更换域名后，旧域名的 `localStorage` 不会自动迁移

详见 [PRIVACY.md](PRIVACY.md)。

## 安全设计

- 首次打开时展示使用前确认：年龄、非治疗边界、数据去向、危机资源
- AI 提示中包含危机安全规则：遇到自伤/自杀/现实危险时停止常规注脚
- 页面始终提供「即时支持」入口
- 对明显的风险词给出提醒
- 接口地址和 CSP 都限制为 DeepSeek 官方端点
- 没有后端、没有共享密钥、没有用户账号系统

## 项目结构

```text
.
├── index.html       # 单文件应用（HTML + CSS + JS）
├── favicon.svg      # 站点图标
├── preview.png      # README 预览图
├── legal.html       # 网页可读版：隐私说明与免责声明
├── 404.html         # GitHub Pages 404 页面
├── DEPLOY.md        # GitHub Pages 发布清单
├── robots.txt
├── README.md
├── LICENSE
├── PRIVACY.md
├── DISCLAIMER.md
├── SECURITY.md
├── .gitignore
└── .nojekyll        # 让 GitHub Pages 直接发布静态文件
```

## 开发

整个应用就是一个 `index.html`，没有构建步骤。

修改后可以直接在本地打开，或启动任意静态服务器：

```bash
python -m http.server 8000
```

然后访问 `http://127.0.0.1:8000/`。

## 浏览器与网络

- 推荐最新版 Chrome / Edge / Safari
- AI 连接使用浏览器直连 DeepSeek；若网络、代理或地区限制导致 CORS/网络失败，页面会提示并回退到本地注脚
- 正式发布后，请在实际 GitHub Pages 域名上重新测试一次连接

## 许可

代码采用 [MIT License](LICENSE)。  
页面中的文字、案例与视觉设计如无特别说明，随项目一并提供；案例为虚构教学材料，不对应真实来访者。

## 危机资源

如果你或你认识的人正处于危险中：

- 急救：**120**
- 报警：**110**
- 全国心理援助热线：**12356**（以当地实际开通情况为准）
- 北京心理危机研究与干预中心：**010-82951332**

请不要独自承担危机干预。联系一个真实的人，去一个有人的地方，先把安全放在第一位。
