# GitHub Pages 发布清单

这份清单把「本地文件夹」变成「可访问的 GitHub Pages 页面」。

## 0. 发布前检查

- [ ] 页面打开时是空白开局，没有测试记录
- [ ] 首次打开会出现使用前确认，两个勾选项都可用
- [ ] 未连接 API 时，本地注脚能正常走完
- [ ] 连接 API 后，测试连接、生成注脚、润色都正常
- [ ] 导出 JSON / Markdown 正常
- [ ] 手机端没有横向溢出
- [ ] 没有提交 API Key、`.env`、真实用户导出文件
- [ ] 案例页明确标注「虚构教学案例」
- [ ] 隐私说明和免责声明能从页面打开

## 1. 建议先改文件夹名

本地文件夹可以叫 `git therapist`，但 GitHub 仓库名不能有空格。  
建议把本地文件夹复制/重命名为：

```text
qixin-therapist/
```

这不影响页面内容。

## 2. 初始化本地 Git 仓库

在文件夹内执行：

```bash
cd "qixin-therapist"
git init -b main
git add .
git commit -m "Initial release: 栖心 V2.1"
```

如果 Git 提示需要身份：

```bash
git config user.name "你的名字"
git config user.email "你的邮箱"
```

## 3. 创建 GitHub 仓库

在 GitHub 新建一个仓库，例如：

```text
qixin-therapist
```

建议：

- Public
- 不要勾选自动创建 README / .gitignore / License（本地已经有了）
- 创建后复制仓库地址

## 4. 推送

```bash
git remote add origin https://github.com/<你的用户名>/qixin-therapist.git
git push -u origin main
```

如果使用 SSH：

```bash
git remote add origin git@github.com:<你的用户名>/qixin-therapist.git
git push -u origin main
```

## 5. 开启 GitHub Pages

1. 打开仓库 **Settings**
2. 左侧选择 **Pages**
3. **Build and deployment → Source** 选择 **Deploy from a branch**
4. Branch 选择 `main`
5. Folder 选择 `/ (root)`
6. 点击 **Save**
7. 等待 1—3 分钟

页面地址通常为：

```text
https://<你的用户名>.github.io/qixin-therapist/
```

## 6. 上线后的必测项

### 基础

- [ ] 页面能在手机和电脑打开
- [ ] 首次打开出现使用前确认
- [ ] 同意后是空白页面，主线显示「尚未形成」
- [ ] 「案例参考」能打开，文字为灰色
- [ ] 隐私说明 / 免责声明能打开

### API

- [ ] 在设置里填入一个**单独的测试 Key**
- [ ] 点击「测试连接」成功
- [ ] 完成一层，能看到流式注脚
- [ ] 测试 401（错误 Key）、429（频繁）、断网时的提示
- [ ] 测完撤销测试 Key
- [ ] 不在公开仓库、issue、截图中留下 Key

### 数据

- [ ] 刷新后记录仍在
- [ ] 导出 JSON 不包含 API Key
- [ ] 导出 Markdown 正常
- [ ] 「重新开始这次」能清空记录
- [ ] 无痕模式下能打开，且不会误以为记录已保存

## 7. 自定义域名（可选）

如果要绑定自定义域名：

- GitHub Pages 设置里填写域名
- 在域名服务商配置 CNAME
- 等待 HTTPS 证书签发

注意：**localStorage 按域名隔离**。  
从 `github.io` 换到自定义域名后，旧域名下的记录不会自动迁移。

## 8. 发布后维护

- 修改文案或功能后，重新测试 API 与手机端
- 如果 DeepSeek API 地址或 CORS 策略变化，页面会提示连接失败，本地模式仍可用
- 不要把任何人的真实练习记录、API Key、导出 JSON 提交到仓库
- 如果收到安全报告，先私下处理，不要在公开 issue 中粘贴敏感信息
