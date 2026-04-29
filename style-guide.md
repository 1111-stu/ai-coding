# UI 风格指南

## 1. 概览

本风格指南基于 `style.md` 中的 CSS 变量与提供的 DeepSeek 对话首页截图整理。代码证据以 `style.md` 为准，截图用于验证页面结构、视觉层级、组件外观和实际渲染效果。截图中可见的界面整体采用浅色、低对比、中性偏蓝灰的背景体系，并以 DeepSeek 蓝作为主品牌色。

主要设计特征：

- 全局为白色主画布，左侧固定浅蓝灰侧栏，中央为对话起始状态。
- 视觉语言以细边框、低透明度阴影、浅色填充、圆角胶囊按钮为主。
- 品牌色存在两套主色表达：`--dsw-static-deepseek-500: #3964fe` 与 `--dsr-main: #4d6bfe`。
- 字体体系使用 `quote-cjk-patch`、`Inter` 和系统字体栈；默认文本为 14px/25px。
- `style.md` 主要提供设计 token 和语义变量，缺少具体组件选择器，因此组件尺寸与状态中部分内容来自截图推断。

## 2. 色彩体系

### 2.1 基础色板

`style.md` 定义了完整的 Tailwind 风格 RGB 色阶，包括 slate、gray、zinc、neutral、stone、red、orange、amber、yellow、lime、green、emerald、teal、cyan、sky、blue、indigo、violet、purple、fuchsia、pink、rose 等。基础色阶以 `--ds-rgb-{color}-{step}` 命名，步进包含 `50` 到 `950`，并包含额外的 `150/250/350/450/550/650/750/850` 中间档。

| 类型 | 变量示例 | 值 | 来源 | 用途 |
| --- | --- | --- | --- | --- |
| 黑色 | `--ds-rgb-black` | `0 0 0` | `style.md:6` | 基础黑色、文本引用 |
| 白色 | `--ds-rgb-white` | `255 255 255` | `style.md:7` | 主背景、前景反色 |
| Slate | `--ds-rgb-slate-50` 至 `--ds-rgb-slate-950` | `248 250 252` 至 `2 6 23` | `style.md:8-26` | 冷灰、图标 hover |
| Neutral | `--ds-rgb-neutral-50` 至 `--ds-rgb-neutral-950` | `250 250 250` 至 `10 10 10` | `style.md:65-83` | 文本、边框、输入背景 |
| Blue | `--ds-rgb-blue-50` 至 `--ds-rgb-blue-950` | `239 246 255` 至 `23 37 84` | `style.md:293-311` | 信息色、基础主色 |
| Red | `--ds-rgb-red-50` 至 `--ds-rgb-red-950` | `254 242 242` 至 `69 10 10` | `style.md:103-121` | 错误、删除 |
| Amber | `--ds-rgb-amber-50` 至 `--ds-rgb-amber-950` | `255 251 235` 至 `69 26 3` | `style.md:141-159` | 警告 |
| Green | `--ds-rgb-green-50` 至 `--ds-rgb-green-950` | `240 253 244` 至 `5 46 22` | `style.md:198-216` | 成功 |

### 2.2 品牌色与主操作色

| 角色 | 变量 | 值 | 来源 | 使用说明 |
| --- | --- | --- | --- | --- |
| DeepSeek 品牌主色 | `--dsw-static-deepseek-500` | `#3964fe` | `style.md:447` | `--dsw-alias-brand-primary`、品牌文字、主按钮基础色 |
| DeepSeek 浅背景 | `--dsw-static-deepseek-50` | `#edf3fe` | `style.md:448` | ghost 按钮 active 填充、气泡浅底 |
| DeepSeek hover | `--dsw-static-deepseek-450` | `#5686fe` | `style.md:446` | `--dsw-alias-button-primary-hover` |
| DeepSeek 辅助高亮 | `--dsw-static-deepseek-200` | `#d3e2ff` | `style.md:443` | 气泡 highlight |
| 应用主色 | `--dsr-main` | `#4d6bfe` | `style.md:666` | 截图中模式按钮、发送按钮、品牌 logo 视觉接近该色，截图验证 |
| 应用主色 40% | `--dsr-main-2` | `rgba(77,107,254,.4)` | `style.md:667` | 半透明主色 |
| 应用主色 20% | `--dsr-main-3` | `rgba(77,107,254,.2)` | `style.md:668` | 二级按钮背景 |

### 2.3 语义色

| 语义 | 变量 | 值 | 来源 | 用途 |
| --- | --- | --- | --- | --- |
| 信息/主色 | `--ds-rgb-info` / `--ds-rgb-primary` | `var(--ds-rgb-blue-500)` | `style.md:636-637` | 信息、链接、主操作基础色 |
| 主色前景 | `--ds-rgb-primary-foreground` | `var(--ds-rgb-white)` | `style.md:638` | 主按钮文字/图标 |
| 错误 | `--ds-rgb-error` | `var(--ds-rgb-red-500)` | `style.md:642` | 错误提示 |
| 警告 | `--ds-rgb-warning` | `var(--ds-rgb-amber-500)` | `style.md:643` | 警告提示 |
| 成功 | `--ds-rgb-success` | `var(--ds-rgb-green-500)` | `style.md:644` | 成功提示 |
| 错误主色 | `--dsw-alias-state-error-primary` | `var(--dsw-static-red-600)` / `#ec1313` | `style.md:493,551` | 强错误状态 |
| 成功主色 | `--dsw-alias-state-success-primary` | `var(--dsw-static-green-500)` / `#22c55e` | `style.md:454,553` | 成功状态 |
| 警告主色 | `--dsw-alias-state-warn-primary` | `var(--dsw-static-amber-500)` / `#f59e0b` | `style.md:428,556` | 警告状态 |

### 2.4 文本、背景与边框

| 角色 | 变量 | 值 | 来源 | 截图表现 |
| --- | --- | --- | --- | --- |
| 主背景 | `--dsw-alias-bg-base` | `var(--dsw-static-neutral-bluish-00)` / `#fff` | `style.md:471,495,701` | 中央画布为白色 |
| 侧栏背景 | `--dsw-specific-sidebar-fill` | `var(--dsw-static-neutral-bluish-50)` / `#f9fafb` | `style.md:478,567` | 截图左侧侧栏为极浅蓝灰 |
| 应用侧栏背景 | `--dsr-side-bg` | `#f9fbff` | `style.md:689` | 与截图侧栏背景接近 |
| 主文本 | `--dsw-alias-label-primary` | `var(--dsw-static-neutral-bluish-1000)` / `#0f1115` | `style.md:472,536` | 标题、主要列表文字 |
| 次级文本 | `--dsw-alias-label-secondary` | `var(--dsw-static-neutral-bluish-700)` / `#61666b` | `style.md:481,537` | 次级信息 |
| 三级文本 | `--dsw-alias-label-tertiary` | `var(--dsw-static-neutral-bluish-600)` / `#81858c` | `style.md:479,538` | 时间分组如“昨天”“7 天内” |
| caption | `--dsw-alias-label-caption` | `var(--dsw-static-neutral-bluish-400)` / `#adb2b8` | `style.md:476,532` | 弱提示/占位 |
| 轻边框 | `--dsw-alias-border-l1` | `rgba(0,0,0,.04)` | `style.md:507` | 极弱分隔线 |
| 默认边框 | `--dsw-alias-border-l2` | `rgba(0,0,0,.1)` | `style.md:509` | 输入框/按钮边界 |
| 输入边框 | `--dsr-input-border` | `#dce0e9` | `style.md:677` | 截图输入框边框接近此值 |

### 2.5 渐变

| 变量 | 值 | 来源 | 用途 |
| --- | --- | --- | --- |
| `--dsw-linear-gradient-sidebar` | `linear-gradient(180deg,rgba(249,250,252,0) 0%,var(--dsw-specific-sidebar-fill)80.65%)` | `style.md:572` | 侧栏底部/滚动遮罩渐变 |
| `--dsw-linear-gradient-think` | `linear-gradient(180deg,#fff 20.19%,rgba(255,255,255,0) 100%)` | `style.md:573` | 思考区域白色淡出 |
| `--dsw-linear-think-select` | `linear-gradient(180deg,#f5f6f7 20.19%,rgba(245,246,247,0) 100%)` | `style.md:574` | 选中思考区域淡出 |

## 3. 字体排版

### 3.1 字体族

| 用途 | 变量 | 值 | 来源 |
| --- | --- | --- | --- |
| 全局 UI 字体 | `--dsw-font-family` | `"quote-cjk-patch","Inter",system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen,Ubuntu,Cantarell,"Open Sans","Helvetica Neue",sans-serif` | `style.md:4` |
| 代码字体 | `--ds-font-family-code` | `Menlo,Monaco,Consolas,"Cascadia Mono","Ubuntu Mono","DejaVu Sans Mono","Liberation Mono","JetBrains Mono","Fira Code",Cousine,"Roboto Mono","Courier New",Courier,sans-serif,system-ui` | `style.md:628` |

全局设置：

- `font-variant-ligatures: no-contextual`，禁用 contextual ligatures，来源 `style.md:5`。
- `font-size: var(--ds-font-size-m)`，默认 14px，来源 `style.md:615,632`。
- `line-height: var(--ds-line-height-m)`，默认 25px，来源 `style.md:616,633`。
- `font-family: var(--dsw-font-family)`，来源 `style.md:635`。
- `-webkit-font-smoothing: antialiased`，来源 `style.md:702`。

### 3.2 UI 字号层级

| Token | 字重 | 字号 | 行高 | 来源 | 用途 |
| --- | --- | --- | --- | --- | --- |
| `--dsw-font-xl-24` | 600 | 24px | 32px | `style.md:596` | 大标题 |
| `--dsw-font-l-20` | 500 | 20px | 28px | `style.md:597` | 一级 UI 标题 |
| `--dsw-font-m-18` | 500 | 16px | 28px | `style.md:598` | 中标题；命名含 18 但实际字号 16px |
| `--dsw-font-base-16` | normal | 16px | 24px | `style.md:599` | 正文/输入 |
| `--dsw-font-base-strong-16` | 500 | 16px | 24px | `style.md:600` | 加重正文 |
| `--dsw-font-s-14` | normal | 14px | 22px | `style.md:601` | 常规 UI 文本 |
| `--dsw-font-s-strong-14` | 500 | 14px | 22px | `style.md:602` | 强调 UI 文本 |
| `--dsw-font-xs-13` | normal | 13px | 20px | `style.md:603` | 次级列表文本 |
| `--dsw-font-xs-strong-13` | 500 | 13px | 20px | `style.md:604` | 次级强调 |
| `--dsw-font-xxs-12` | normal | 12px | 18px | `style.md:605` | 标签、按钮小字 |
| `--dsw-font-xxxs-11` | normal | 11px | 16px | `style.md:607` | 极弱辅助信息 |

### 3.3 Markdown 排版

| Token | 值 | 来源 |
| --- | --- | --- |
| `--dsw-font-markdown-h1` | `700 24px/34px var(--dsw-font-family)` | `style.md:580` |
| `--dsw-font-markdown-h2` | `700 22px/32px var(--dsw-font-family)` | `style.md:581` |
| `--dsw-font-markdown-h3` | `700 20px/30px var(--dsw-font-family)` | `style.md:582` |
| `--dsw-font-markdown-h4` | `600 16px/28px var(--dsw-font-family)` | `style.md:583` |
| `--dsw-font-markdown-base` | `16px/28px var(--dsw-font-family)` | `style.md:584` |
| `--dsw-font-markdown-table` | `15px/25px var(--dsw-font-family)` | `style.md:588` |
| `--dsw-font-markdown-small` | `14px/24px var(--dsw-font-family)` | `style.md:590` |
| `--dsw-font-markdown-code` | `14px/22px var(--ds-font-family-code)` | `style.md:594` |
| `--dsw-font-markdown-code-block` | `13px/22px var(--ds-font-family-code)` | `style.md:595` |

### 3.4 截图中的排版观察

- 中央标题“使用快速模式开始对话”视觉约为 24px、600 左右，和 `--dsw-font-xl-24` 对应；此处为截图推断。
- 侧栏会话列表文本视觉约 14px，行高宽松，和 `--dsw-font-s-14` / 全局 `--ds-font-size-m` 接近；此处为截图推断。
- 分组时间文本如“昨天”“7 天内”颜色弱、字号更小，视觉接近 12px 或 13px；此处为截图推断。

## 4. 间距系统

`style.md` 没有提供完整 spacing token，但提供了关键布局变量和输入高度变量。截图显示实际界面遵循 8px 左右的节奏，并在大容器上使用更大的水平留白。

| 变量/观察 | 值 | 来源 | 用途 |
| --- | --- | --- | --- |
| `--message-list-padding-horizontal` | `44px` | `style.md:2` | 消息列表水平内边距 |
| `--message-list-max-width` | `840px` | `style.md:3` | 消息列表最大宽度 |
| `--ds-input-height-l` | `44px` | `style.md:609` | 大号输入/表单高度 |
| `--ds-input-height-m` | `34px` | `style.md:610` | 中号输入/按钮高度 |
| `--ds-input-height-s` | `30px` | `style.md:611` | 小号输入/按钮高度 |
| `--ds-input-height-xs` | `26px` | `style.md:612` | 极小输入/按钮高度 |
| 侧栏内边距 | 约 12px-22px | 截图推断 | logo、按钮、列表与边界间距 |
| 中央输入框宽度 | 约 780px | 截图推断 | 与 840px 最大内容宽接近 |
| 模式切换按钮间距 | 约 8px | 截图推断 | 快速模式/专家模式之间 |

建议使用规则：

- 小控件内部垂直空间优先参考 `26px/30px/34px/44px` 高度体系。
- 页面主内容宽度优先参考 `--message-list-max-width: 840px`。
- 消息区域水平内边距优先参考 `44px`。
- 截图中的胶囊按钮、标签按钮显示了 8px 左右的横向间隔，此值仅为推断。

## 5. 布局与栅格

| 布局对象 | 值 | 来源 | 说明 |
| --- | --- | --- | --- |
| 侧栏宽度 | `--sider-width: 261px` | `style.md:1` | 截图左侧侧栏固定宽度，与视觉宽度一致 |
| 消息列表最大宽 | `--message-list-max-width: 840px` | `style.md:3` | 中央消息/输入区域约束 |
| 消息列表水平 padding | `44px` | `style.md:2` | 内容与容器边缘间距 |
| 应用高度 | `--app-height: 1318px` | `style.md:712` | 当前环境/视口记录值，不建议作为通用 token |
| Mermaid 高度 | `--mermaid-height: 360px` | `style.md:704` | 图表固定高度 |
| Mermaid 最大高度 | `--mermaid-max-height: 40vh` | `style.md:705` | 图表视口约束 |

截图布局验证：

- 左侧为固定宽侧栏，顶部 logo，中部为按时间分组的会话列表，底部为用户入口。
- 主区域空白占比大，核心起始模块居中偏下，输入框位于标题和模式切换下方。
- 输入区采用横向居中布局，视觉宽度明显小于主画布，接近 `--message-list-max-width`。
- 侧栏与主画布之间存在非常轻的分隔感，来源可能是背景色差而非明显边框；此处为截图推断。

## 6. 组件样式

### 6.1 侧栏

| 项 | 值 | 来源 | 说明 |
| --- | --- | --- | --- |
| 宽度 | `261px` | `style.md:1` | 固定侧栏 |
| 背景 | `--dsw-specific-sidebar-fill` = `#f9fafb` / `--dsr-side-bg: #f9fbff` | `style.md:478,567,689` | 代码存在两套接近的侧栏背景 |
| Hover 背景 | `--dsw-specific-sidebar-nav-item-hover` = `#f1f3f5` | `style.md:483,570` | 侧栏导航 hover |
| Active 背景 | `--dsw-specific-sidebar-nav-item-active` = `#ebeef2` | `style.md:473,569` | 侧栏导航 active |
| Active accent | `--dsw-specific-sidebar-nav-item-active-accent` = `#e4edfd` | `style.md:442,568` | 激活强调 |
| 侧栏渐变 | `--dsw-linear-gradient-sidebar` | `style.md:572` | 用于滚动/底部淡出 |

截图中“开启新对话”按钮为白色胶囊，带弱阴影/边框；具体 CSS 未在 `style.md` 中出现，圆角和阴影为截图推断。

### 6.2 模式切换按钮

| 状态 | 背景/边框/文字 | 来源 | 截图验证 |
| --- | --- | --- | --- |
| 快速模式 active | 背景接近 `--dsw-alias-button-ghost-active-fill` = `#edf3fe`，边框接近 `--dsw-alias-button-ghost-active-border` = `#b7c8fe` | `style.md:519-520` | 截图中快速模式为浅蓝胶囊并带蓝色边框 |
| active hover | `--dsw-alias-button-ghost-active-hover` = `#e4edfd` | `style.md:521` | 未提供 hover 截图 |
| 专家模式 inactive | 背景白色或透明，边框弱灰 | 截图推断，相关边框见 `style.md:507-509` | 截图中专家模式为白色胶囊 |
| 主色文字/图标 | `--dsr-main: #4d6bfe` 或 `--dsw-alias-brand-primary: #3964fe` | `style.md:512-514,666` | 截图中 active 文本和图标为亮蓝 |

### 6.3 输入框 / 消息输入区

| 项 | 值 | 来源 | 说明 |
| --- | --- | --- | --- |
| 主输入背景 | `--dsw-specific-input-major: #fff` | `style.md:563` | 截图输入框为白色 |
| 输入 token | `--ds-rgb-input: var(--ds-rgb-neutral-100)` | `style.md:653` | 一般输入背景 |
| 强输入 token | `--ds-rgb-input-strong: var(--ds-rgb-neutral-150)` | `style.md:654` | 较强输入背景 |
| focus 背景 | `--ds-rgb-input-focus: var(--ds-rgb-white)` | `style.md:655` | 聚焦白色 |
| 输入边框 | `--dsr-input-border: #dce0e9` | `style.md:677` | 截图输入框边框接近 |
| 大号输入高度 | `44px` | `style.md:609` | 输入区整体比 44px 高，可能为多行容器；控件高度可复用 |

截图中输入框是大圆角容器，内部上方占位文字“给 DeepSeek 发送消息”，底部左侧有功能按钮，右侧有附件和发送按钮；容器圆角、具体 padding、总高度缺少代码证据，属于截图推断。

### 6.4 按钮

| 类型 | Token | 值 | 来源 |
| --- | --- | --- | --- |
| 主按钮填充 | `--dsw-alias-button-primary-fill` | `var(--dsw-alias-brand-primary)` / `#3964fe` | `style.md:513,523` |
| 主按钮 hover | `--dsw-alias-button-primary-hover` | `#5686fe` | `style.md:446,524` |
| 主按钮 dimmed | `--dsw-alias-button-primary-dimmed` | `#679efe` | `style.md:445,522` |
| 对比按钮 | `--dsw-alias-button-contrast-fill` | `#61666b` | `style.md:481,515` |
| 浮层按钮 | `--dsw-alias-button-floating-fill` | `#fff` | `style.md:471,517` |
| 浮层按钮 hover | `--dsw-alias-button-floating-hover` | `#f1f3f5` | `style.md:483,518` |
| 工具栏按钮 | `--dsw-alias-button-tool-bar-fill` | `rgba(84,85,87,.5)` | `style.md:526` |
| 工具栏按钮 hover | `--dsw-alias-button-tool-bar-hover` | `rgba(84,85,87,.6)` | `style.md:527` |

截图验证：

- 发送按钮为圆形浅蓝按钮，图标白色或接近白色；具体背景更接近浅蓝/主色低透明态，代码中没有直接的发送按钮选择器，属截图推断。
- 输入框底部的“深度思考”“智能搜索”为小号浅蓝胶囊按钮，视觉接近 `--dsw-alias-button-ghost-active-fill` 和 `--dsw-alias-button-ghost-active-border`。

### 6.5 标签、提示、Markdown 与菜单

| 组件/用途 | Token | 值 | 来源 |
| --- | --- | --- | --- |
| tooltip 背景 | `--dsw-alias-tooltip-bg` | `#2c2c2e` | `style.md:485,560` |
| tooltip 前景 | `--dsr-tooltip-fg` | `#eff6ff` | `style.md:687` |
| toast 背景 | `--dsw-alias-toast-bg` | `#353638` | `style.md:484,559` |
| 菜单背景 | `--dsw-specific-menu` | `var(--dsw-alias-bg-layer-3)` / `#fff` | `style.md:498,565` |
| 标签背景 | `--ds-rgb-tag` | `var(--ds-rgb-neutral-200)` | `style.md:657` |
| Markdown inline code | `--dsw-alias-markdown-inline-code` | `#ebeef2` | `style.md:473,544` |
| Markdown code block | `--dsw-alias-markdown-code-block` | `#f9fafb` | `style.md:478,541` |

## 7. 阴影与层级

### 7.1 阴影 token

| 层级 | 变量 | 值 | 来源 | 用途判断 |
| --- | --- | --- | --- | --- |
| LV1 | `--dsw-shadow-lv1` | `0 2px 4px 0 rgba(0,0,0,.05)` | `style.md:575` | 轻微卡片/按钮抬升 |
| LV1 blur | `--dsw-shadow-lv1-blur` | `0 4px 12px 0 rgba(0,0,0,.02)` | `style.md:576` | 大面积柔和浮层 |
| LV2 | `--dsw-shadow-lv2` | `0 4px 12px 0 rgba(0,0,0,.02),0 2px 8px 0 rgba(0,0,0,.04)` | `style.md:577` | 下拉、浮层、输入容器可能使用 |
| LV3 | `--dsw-shadow-lv3` | `0 0 1px 0 rgba(0,0,0,.2),0 0 4px 0 rgba(0,0,0,.02),0 12px 32px 0 rgba(0,0,0,.08)` | `style.md:578` | 高层级弹窗/菜单 |

### 7.2 层级与遮罩

| Token | 值 | 来源 | 用途 |
| --- | --- | --- | --- |
| `--dsw-alias-bg-mask-1` | `rgba(0,0,0,.24)` | `style.md:499` | 基础遮罩 |
| `--dsw-alias-bg-mask-2` | `rgba(0,0,0,.12)` | `style.md:500` | 轻遮罩 |
| `--dsw-alias-bg-mask-3` | `rgba(0,0,0,.48)` | `style.md:501` | 强遮罩 |
| `--dsw-alias-bg-mask-photo` | `rgba(0,0,0,.88)` | `style.md:502` | 图片预览遮罩 |
| `--dsw-mask-blur` | `blur(2px)` | `style.md:579` | 遮罩模糊 |

未在当前材料中发现明确的 `z-index` token 或组件层级数值。

## 8. 动画与过渡

| Token | 值 | 来源 | 用途 |
| --- | --- | --- | --- |
| `--ds-transition-duration-fast` | `.1s` | `style.md:630` | 快速反馈 |
| `--ds-transition-duration` | `.2s` | `style.md:629` | 默认交互过渡 |
| `--ds-transition-duration-slow` | `.3s` | `style.md:631` | 较慢展开/消退 |
| `--ds-ease-in-out` | `cubic-bezier(.4,0,.2,1)` | `style.md:625` | 标准进出缓动 |
| `--ds-ease-in` | `cubic-bezier(.4,0,1,1)` | `style.md:626` | 进入/收起 |
| `--ds-ease-out` | `cubic-bezier(0,0,.2,1)` | `style.md:627` | 出现/展开 |

截图没有展示动态过程，因此具体组件触发场景未能验证。根据变量命名，hover、active、菜单、浮层、按钮状态应优先使用 `.2s` 默认时长和 `--ds-ease-in-out`。

## 9. 圆角

`style.md` 未提供明确的 radius token 或 `border-radius` 规则。

截图推断：

- “开启新对话”、模式切换、输入框功能按钮均为胶囊形态，圆角接近高度的一半。
- 中央输入框为大圆角矩形，视觉圆角约 20px-24px。
- 发送按钮为圆形按钮。

由于缺少代码证据，上述圆角值均标记为推断，不应直接作为项目 token 固化；建议补充 radius 变量或组件 CSS 后再确定。

## 10. 不透明度与透明效果

| Token | 值 | 来源 | 用途 |
| --- | --- | --- | --- |
| `--dsw-alias-bg-mask-1` | `rgba(0,0,0,.24)` | `style.md:499` | 遮罩 |
| `--dsw-alias-bg-mask-2` | `rgba(0,0,0,.12)` | `style.md:500` | 轻遮罩 |
| `--dsw-alias-bg-mask-3` | `rgba(0,0,0,.48)` | `style.md:501` | 强遮罩 |
| `--dsw-alias-bg-mask-photo` | `rgba(0,0,0,.88)` | `style.md:502` | 图片遮罩 |
| `--dsw-alias-bg-skeleton` | `rgba(0,0,0,.04)` | `style.md:504` | 骨架屏 |
| `--dsw-alias-border-l1` | `rgba(0,0,0,.04)` | `style.md:507` | 细边框 |
| `--dsw-alias-border-l2` | `rgba(0,0,0,.1)` | `style.md:509` | 常规边框 |
| `--dsw-alias-border-l3` | `rgba(0,0,0,.12)` | `style.md:510` | 强边框 |
| `--dsw-alias-border-l4` | `rgba(0,0,0,.16)` | `style.md:511` | 更强边框 |
| `--dsw-alias-interactive-bg-hover` | `rgba(38,49,72,.06)` | `style.md:531` | 常规 hover |
| `--dsw-alias-interactive-bg-active` | `rgba(38,49,72,.1)` | `style.md:528` | active |
| `--dsw-alias-interactive-bg-hover-accent` | `rgba(38,49,72,.14)` | `style.md:529` | 强 hover |
| `--dsw-alias-interactive-bg-hover-danger` | `rgba(236,19,19,.05)` | `style.md:530` | 危险 hover |
| `--scroll-color` | `rgba(0,0,0,.08)` | `style.md:708` | 滚动条 |
| `--scroll-color-hover` | `rgba(0,0,0,.15)` | `style.md:709` | 滚动条 hover |
| `--dsr-risk-border` | `rgba(228,119,61,.1)` | `style.md:698` | 风险边框 |
| `--dsr-risk-fill` | `rgba(228,119,61,.05)` | `style.md:699` | 风险背景 |

整体透明度规律：

- 边框使用 `0.04/0.1/0.12/0.16` 的黑色透明度阶梯。
- hover/active 使用深蓝灰 `rgba(38,49,72,...)`，透明度为 `.06/.1/.14`。
- 危险态 hover 使用红色 `rgba(236,19,19,.05)`。
- 工具栏按钮使用中性深灰半透明 `.36/.5/.6`，来源 `style.md:525-527`。

## 11. 异常与不一致项

| 类型 | 位置/来源 | 当前值 | 相关规范 | 问题 | 建议 |
| --- | --- | --- | --- | --- | --- |
| 主色双轨 | `style.md:447,513,666,679` | `#3964fe` 与 `#4d6bfe` | 品牌主色/应用主色 | `--dsw-*` 与 `--dsr-*` 两套主色并存，截图中更接近 `#4d6bfe` | 明确 `--dsw-static-deepseek-500` 与 `--dsr-main` 的使用边界，或建立单一 alias |
| 字体 token 命名不一致 | `style.md:598` | `--dsw-font-m-18: 500 16px/28px` | 字号层级 | 变量名含 `18`，实际字号为 `16px` | 核对命名是否历史遗留，避免开发者误用 |
| 一次性全局颜色 | `style.md:703` | `color: purple` | 全局文本色应来自 label token | `purple` 不属于当前语义色/品牌色体系，且可能影响全局继承 | 如非调试代码，应改为 `--dsw-alias-label-primary` 或具体语义 token |
| 删除色命名异常 | `style.md:450` | `--dsw-static-deepseek-700-delete: #2f4c8f` | DeepSeek 品牌色阶 | 变量名包含 `delete`，但颜色仍属于 DeepSeek 蓝色阶，不像危险/删除色 | 若仅为废弃 token，建议标注 deprecated；危险删除应使用 red token |
| 圆角缺少 token | 截图 + `style.md` | 截图大量胶囊/圆形按钮，但 CSS 无 radius token | 组件圆角规范 | 无法从代码确认圆角等级，影响复用准确性 | 补充 `radius` token 或提供组件 CSS |
| 组件选择器不足 | `style.md` 全文 | 多为变量，无具体按钮/输入框选择器 | 组件样式规范 | 无法确认 hover/focus/disabled 的完整实现 | 导出组件 CSS 或 Tailwind 类名以完善状态指南 |
| 应用高度疑似环境值 | `style.md:712` | `--app-height: 1318px` | 布局 token | 看起来像当前视口运行时值，不像可复用设计 token | 不建议纳入通用规范，除非用于移动端视口修正 |
