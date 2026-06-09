# Project: Fish Fish Wanna Fish Ahh

HTML5 Canvas 游戏，单文件架构（`index.html`），包含钓鱼阶段与寿司餐厅管理阶段。

## Tech Stack

- Pure HTML5 / Vanilla JavaScript / Canvas 2D API
- No framework, no build tool, no bundler
- Single file: `index.html`

## Frontend Design Guidelines

以下规范在所有 UI/视觉相关修改中自动适用，无需额外调用指令。

### Canvas UI 原则

- 所有 HUD 元素（血条、货币、氧气值）使用统一的字体大小阶梯：`12px / 16px / 20px / 28px`
- 文字颜色在深色背景上用 `#FFFFFF` 或 `rgba(255,255,255,0.9)`，深色文字用 `#1a1a2e`
- HUD 区块之间保持 `8px` 最小间距，避免信息堆叠
- 点击/交互元素的视觉反馈时间控制在 100–200ms

### 色彩系统

- 浅海区：`#87CEEB`（天空蓝）系
- 珊瑚礁区：`#FF7F50`（珊瑚橙）+ `#20B2AA`（海绿）系
- 深海区：`#0d1b2a` → `#1b4f72` 渐变
- 货币/奖励提示：`#FFD700`（金色）
- 危险/警告（鲨鱼、氧气不足）：`#FF4444`

### 响应式与分辨率

- Canvas 尺寸应随窗口 resize 自适应，保持宽高比
- 触屏设备需支持 `touchstart` / `touchmove` 作为鼠标事件的 fallback

### 可访问性（最低要求）

- 重要游戏状态变化（阶段切换、游戏结束）加 `aria-live` 文字提示
- 避免纯色区分（色盲友好），配合形状或图案区分鱼种

### 代码规范

- JS 函数命名用 camelCase，常量用 UPPER_SNAKE_CASE
- 渲染函数以 `draw` 开头（如 `drawFish`、`drawHUD`）
- 更新逻辑函数以 `update` 开头（如 `updateOxygen`）
- 避免在 `requestAnimationFrame` 回调中做 DOM 操作

## Frontend Design Skill

本项目已安装 `frontend-design` skill（`~/.claude/skills/frontend-design.md`）。

在处理以下任务时，自动应用该 skill 的设计原则，无需手动调用 `/frontend-design`：

- 修改或新增 Canvas 绘制函数
- 调整 HUD、菜单、对话框等 UI 元素
- 新增动画或粒子效果
- 修改色彩、字体、布局相关代码

## Cartoon Customer Skill

本项目已安装 `cartoon-customer` skill（`~/.claude/skills/cartoon-customer.md`）。

修改或新增顾客绘制相关代码时，自动应用该 skill 的规范：

- `drawCustomer(ctx, c, x, y)` 原点为角色**脚底中心**
- 4 种 style：business / casual / lady / old，通过 `c.style` 指定
- 眼睛必须是：眼白椭圆 + 彩色虹膜 + 黑瞳孔 + 白高光，禁止纯色圆替代
- 所有部位加 `strokeStyle` 描边增强卡通感
