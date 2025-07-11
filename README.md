# IP 自动采集器

每3小时自动采集以下网站的优选 IP 地址，生成 `ip.txt` 文件：

- [GACJIE 监控 - Cloudflare IPv4](https://monitor.gacjie.cn/page/cloudflare/ipv4.html)
- [IP 优选列表](https://ip.164746.xyz)

同时支持以下 JS 动态生成的 IP 检测页面：
- [CF 优选检测](https://cf.090227.xyz)
- [CloudFlareYes](https://stock.hostmonit.com/CloudFlareYes)

## 项目结构
```
.
├── .github/
│   └── workflows/
│       └── main.yml       # GitHub Actions 工作流配置
├── collect_ips.py         # IP 采集脚本
├── ip.txt                 # 自动生成的 IP 列表
└── README.md              # 当前文档
```

## 工作流程说明

### 定时任务
- 每3小时自动触发一次采集任务
- 支持手动触发更新
- 代码提交时也可触发更新（需取消注释配置）

### 技术栈
- 编程语言：Python 3.9
- 主要依赖：requests, beautifulsoup4
- 自动化工具：GitHub Actions

### 数据处理流程
1. 发送 HTTP 请求获取网页内容
2. 使用 BeautifulSoup 解析 HTML
3. 通过正则表达式提取 IP 地址
4. 去重并保存到 `ip.txt`
5. 自动提交更新到 GitHub 仓库

## 使用说明
1. 点击仓库右上角的 **Star** 支持本项目
2. 如需自定义采集源，请修改 `collect_ips.py` 中的 URL 列表
3. 可通过修改 `main.yml` 调整采集频率
4. 查看 `ip.txt` 获取最新 IP 列表

## 贡献指南
1. Fork 本仓库
2. 创建你的特性分支 (`git checkout -b feature/fooBar`)
3. 提交你的更改 (`git commit -am 'Add some fooBar'`)
4. 将分支推送到 GitHub (`git push origin feature/fooBar`)
5. 创建新的 Pull Request

## 免责声明
- 本项目仅用于学习和研究目的
- 请遵守相关网站的使用条款
- 请勿将采集的 IP 用于非法活动
- 作者不对任何不当使用负责

## 许可证
本项目采用 MIT 许可证 - 详情请参阅 [LICENSE](LICENSE) 文件
