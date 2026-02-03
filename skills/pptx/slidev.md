# Slidev Workflow

Slidev 是一个基于 Markdown 的演示文稿工具，特别适合技术演示和开发者分享。

## 适用场景

- 技术分享 / 开发者演讲
- 包含代码演示的内容
- 需要实时交互效果
- 开源项目介绍

## 快速开始

### 1. 初始化项目

```bash
npm init slidev@latest my-presentation
cd my-presentation
```

或在现有目录创建：

```bash
npm install @slidev/cli @slidev/theme-default
```

### 2. 创建 slides.md

```markdown
---
theme: default
title: 演示文稿标题
info: |
  演示文稿描述
class: text-center
drawings:
  persist: false
transition: slide-left
---

# 第一页标题

副标题或描述

---

# 第二页

- 要点一
- 要点二
- 要点三

---
layout: two-cols
---

# 左侧内容

这是左栏的内容

::right::

# 右侧内容

这是右栏的内容

---
layout: center
class: text-center
---

# 居中大标题

用于强调或章节分隔

---

# 代码展示

支持语法高亮和行号

```python {1-3|4-6|all}
def hello():
    print("Hello")
    return True

def world():
    print("World")
```

---
layout: image-right
image: ./image.png
---

# 图片布局

左侧文字，右侧图片

---

# 感谢

<div class="pt-12">
  <span class="px-2 py-1">
    联系方式 / Q&A
  </span>
</div>
```

## 核心语法

### 幻灯片分隔

使用 `---` 分隔幻灯片：

```markdown
# 第一页
内容

---

# 第二页
内容
```

### 常用布局

| 布局 | 用途 |
|------|------|
| `default` | 标准布局 |
| `center` | 内容居中 |
| `two-cols` | 双栏布局 |
| `image-right` | 右侧图片 |
| `image-left` | 左侧图片 |
| `image` | 全屏背景图 |
| `quote` | 引用样式 |
| `section` | 章节分隔页 |
| `fact` | 突出数据/事实 |

### 代码高亮

```markdown
```ts {2,3}
function add(a: number, b: number) {
  const sum = a + b  // 高亮这两行
  return sum
}
```
```

逐步展示代码：

```markdown
```python {1|2-3|all}
import os           # 第一步显示
path = os.getcwd()  # 第二步显示
print(path)         # 第二步显示
```                 # all 显示全部
```

### 动画效果

使用 `v-click` 实现逐步展示：

```markdown
<v-click>

- 点击后显示的内容

</v-click>

<v-clicks>

- 第一个
- 第二个
- 第三个

</v-clicks>
```

### 演讲者备注

```markdown
---

# 幻灯片内容

这是观众看到的内容

<!--
这是演讲者备注
- 提醒自己的要点
- 时间控制
-->
```

## 主题选择

### 官方主题

```yaml
---
theme: default    # 默认主题
theme: seriph     # 优雅简约
theme: apple-basic # Apple 风格
theme: bricks     # 砖块风格
---
```

### 安装第三方主题

```bash
npm install slidev-theme-主题名
```

常用主题：
- `slidev-theme-geist` - Vercel 风格
- `slidev-theme-penguin` - 简洁现代
- `slidev-theme-dracula` - 暗色主题

## 导出

### 导出 PDF

```bash
npx slidev export
```

### 导出 PPTX

```bash
npx slidev export --format pptx
```

### 导出选项

```bash
# 指定文件
npx slidev export slides.md

# 带暗色模式
npx slidev export --dark

# 指定输出文件名
npx slidev export --output my-slides.pdf
```

## 预览和开发

### 启动开发服务器

```bash
npx slidev
```

默认访问 http://localhost:3030

### 快捷键

| 按键 | 功能 |
|------|------|
| `Space` / `→` | 下一页 |
| `←` | 上一页 |
| `o` | 幻灯片概览 |
| `d` | 暗色模式切换 |
| `g` | 跳转到指定页 |

## 工作流程

1. **分析内容** - 确定演示主题和结构
2. **选择主题** - 根据内容风格选择合适的主题
3. **创建 slides.md** - 编写 Markdown 内容
4. **预览调整** - `npx slidev` 实时预览
5. **导出** - 根据需要导出 PDF 或 PPTX

## 与 PowerPoint 方式对比

| 维度 | Slidev | PowerPoint (html2pptx) |
|------|--------|------------------------|
| 输入 | Markdown | HTML |
| 代码高亮 | ✅ 原生支持 | ❌ 需要截图 |
| 动画 | ✅ CSS/Vue | ⚠️ 有限 |
| 输出格式 | Web/PDF/PPTX | PPTX |
| 版本控制 | ✅ Git 友好 | ❌ 二进制 |
| 协作 | ✅ 易于协作 | ⚠️ 需要工具 |
| 离线分享 | ⚠️ 需导出 | ✅ 直接发送 |

## 依赖

```bash
# 全局安装 (推荐)
npm install -g @slidev/cli

# 或项目级安装
npm install @slidev/cli @slidev/theme-default
```

## 示例项目结构

```
my-presentation/
├── slides.md          # 主要内容
├── components/        # 自定义 Vue 组件
│   └── Counter.vue
├── public/            # 静态资源
│   └── image.png
├── styles/            # 自定义样式
│   └── index.css
└── package.json
```
