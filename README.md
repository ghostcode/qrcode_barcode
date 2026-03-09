# 条形码与二维码生成器

一个功能丰富、界面精美的条形码与二维码在线生成工具。采用深色科技风格设计，支持实时预览、历史记录、多格式导出等功能。

<img width="1230" height="754" alt="image" src="https://github.com/user-attachments/assets/47331733-cbab-4078-bf68-8cf854ff7fae" />


---

## 功能亮点

### 条形码生成器

| 功能 | 说明 |
|------|------|
| 多格式支持 | CODE128、CODE39、EAN-13、EAN-8、UPC-A、ITF-14、Pharmacode |
| 尺寸调节 | 宽度4档可选，高度40-200px无级调节 |
| 颜色自定义 | 线条颜色与背景颜色独立设置，支持取色器和手动输入 |
| 显示选项 | 可选显示/隐藏底部文字、启用扁平模式 |
| 格式验证 | 自动校验内容是否符合所选条形码格式规范 |

### 二维码生成器

| 功能 | 说明 |
|------|------|
| 灵活内容 | 支持URL、纯文本、联系方式等任意内容 |
| 尺寸调节 | 128-512px 范围可调 |
| 容错级别 | L(7%)、M(15%)、Q(25%)、H(30%) 四档可选 |
| 样式切换 | 方块、圆角、圆点三种视觉风格 |
| Logo嵌入 | 支持上传自定义Logo，可调节大小比例 |
| 边距控制 | 0-10单位边距调节 |

### 通用功能

- **实时预览** - 输入内容即时生成，无需手动刷新
- **剪贴板复制** - 一键复制生成的图片到剪贴板
- **多格式导出** - 支持 PNG 高清图片和 SVG 矢量格式下载
- **历史记录** - 自动保存最近12条生成记录，支持一键恢复
- **数据持久化** - 使用 localStorage 保存历史和统计数据
- **响应式设计** - 完美适配桌面端和移动端设备

---

## 技术栈

| 类别 | 技术 |
|------|------|
| 核心语言 | HTML5、CSS3、JavaScript (ES6+) |
| 样式框架 | Tailwind CSS 3.x (CDN) |
| 条形码库 | JsBarcode 3.11.6 |
| 二维码库 | qrcode-generator 1.4.4 |
| 字体 | Space Grotesk (标题)、JetBrains Mono (代码) |

---

## 快速开始

### 在线使用

直接在浏览器中打开 `index.html` 文件即可使用，无需安装任何依赖。

### 本地部署

```bash
# 克隆项目
git clone https://github.com/ghostcode/qrcode_barcode.git

# 进入项目目录
cd qrcode_barcode

# 使用任意 HTTP 服务器运行，例如：
# Python 3
python -m http.server 8080

# Node.js (需安装 http-server)
npx http-server -p 8080

# 或直接用浏览器打开 index.html
```

### 集成到现有项目

将以下代码添加到你的 HTML 文件中：

```html
<!-- 外部依赖 -->
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://cdn.jsdelivr.net/npm/jsbarcode@3.11.6/dist/JsBarcode.all.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/qrcode-generator@1.4.4/qrcode.min.js"></script>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

---

## 文件结构

```
qrcode_barcode/
├── index.html          # 主页面（包含 HTML/CSS/JS）
├── README.md           # 项目说明文档
└── assets/             # 资源文件（可选）
    └── images/         # 图片资源
```

> 注：本项目采用单文件架构，所有代码集成在 `index.html` 中，便于部署和分发。

---

## API 参考

### 条形码生成

```javascript
// 使用 JsBarcode 生成条形码
JsBarcode(svgElement, content, {
  format: 'CODE128',      // 条形码格式
  width: 2,               // 条纹宽度
  height: 100,            // 条码高度
  lineColor: '#000000',   // 线条颜色
  background: '#ffffff',  // 背景颜色
  displayValue: true,     // 是否显示文字
  margin: 10              // 边距
});
```

### 二维码生成

```javascript
// 使用 qrcode-generator 生成二维码
const qr = qrcode(0, 'M');  // 类型0(自动), 容错级别M
qr.addData('https://example.com');
qr.make();

// 获取模块数量
const moduleCount = qr.getModuleCount();

// 检查模块是否为深色
qr.isDark(row, col);  // 返回 boolean
```

---

## 浏览器支持

| 浏览器 | 最低版本 |
|--------|----------|
| Chrome | 60+ |
| Firefox | 55+ |
| Safari | 12+ |
| Edge | 79+ |
| Opera | 47+ |

> 注：需要支持 ES6、Clipboard API、Canvas API 的现代浏览器。

---

## 配置选项

### CSS 变量

可通过修改 CSS 变量自定义主题配色：

```css
:root {
  --bg: #0a0f1a;              /* 主背景色 */
  --bg-elevated: #111827;     /* 抬升背景色 */
  --card: rgba(17, 24, 39, 0.8);  /* 卡片背景 */
  --border: rgba(56, 189, 248, 0.15);  /* 边框颜色 */
  --fg: #f1f5f9;              /* 前景文字色 */
  --muted: #64748b;           /* 次要文字色 */
  --accent: #38bdf8;          /* 强调色 */
  --accent-glow: rgba(56, 189, 248, 0.4);  /* 强调色发光 */
  --success: #22c55e;         /* 成功状态色 */
  --warning: #f59e0b;         /* 警告状态色 */
}
```

### 条形码格式说明

| 格式 | 字符要求 | 用途 |
|------|----------|------|
| CODE128 | 全ASCII字符 | 物流、仓储通用 |
| CODE39 | 数字+大写字母 | 工业、国防 |
| EAN-13 | 13位数字 | 国际商品标识 |
| EAN-8 | 8位数字 | 小商品标识 |
| UPC-A | 12位数字 | 北美商品标识 |
| ITF-14 | 14位数字 | 物流外箱 |
| Pharmacode | 3-131070数字 | 医药行业 |

### 二维码容错级别

| 级别 | 恢复能力 | 适用场景 |
|------|----------|----------|
| L | 7% | 清晰环境 |
| M | 15% | 一般环境（推荐） |
| Q | 25% | 可能污损 |
| H | 30% | 嵌入Logo |

---

## 无障碍支持

- 语义化 HTML 标签
- ARIA 属性支持
- 键盘可访问
- 焦点状态可见
- 遵循 `prefers-reduced-motion` 媒体查询

---

## 已知限制

1. **Logo 上传** - 仅支持图片格式，SVG 需转换为位图
2. **历史记录** - 数据存储在 localStorage，清除浏览器数据会丢失
3. **条形码验证** - 部分 format 需要特定长度和校验位
4. **跨域限制** - 本地 file:// 协议下剪贴板功能可能受限

---

## 更新日志

### v1.0.0 (2026-03)

- 初始版本发布
- 支持条形码和二维码生成
- 实现历史记录功能
- 添加 Logo 嵌入支持
- 响应式布局优化

---

## 开发计划

- [ ] 批量生成功能
- [ ] 更多二维码样式（渐变色、自定义图案）
- [ ] 条形码/二维码解码功能
- [ ] 云端历史同步
- [ ] PWA 离线支持
- [ ] 多语言国际化

---

## 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

---

## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。

---

## 致谢

- [JsBarcode](https://github.com/lindell/JsBarcode) - 强大的条形码生成库
- [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) - 轻量级二维码生成库
- [Tailwind CSS](https://tailwindcss.com/) - 实用优先的 CSS 框架
- [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) - 现代几何无衬线字体
- [JetBrains Mono](https://www.jetbrains.com/lp/mono/) - 开发者专用等宽字体

---
10. **贡献指南** - 开源协作流程

文档采用清晰的 Markdown 格式，包含表格、代码块、列表等元素，方便开发者快速了解和使用项目。
