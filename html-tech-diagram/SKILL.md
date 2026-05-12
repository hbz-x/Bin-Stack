---
name: html-tech-diagram
description: Generate self-contained HTML technical diagrams for code flows, system architectures, data structures, state machines, and any process with sequential or branching logic. Triggers on "html流程图", "html图", "生成html", "代码流程图", "系统架构图", "状态图", "流程图", "code flow diagram", "html diagram", "architecture diagram".
metadata:
  version: 1.1.0
---

# HTML Technical Diagram Generator

生成自包含的 HTML 技术示意图，无需任何外部依赖，浏览器直接打开即可查看。适用于任何包含流程、分支、状态转换的代码逻辑或系统架构的可视化，包括但不限于：代码执行流程、请求处理管线、状态机、数据流转、模块交互、算法步骤、系统架构等。

## Workflow

1. **分析内容**：识别主题涉及的层次结构、流程步骤、数据格式、分支条件
2. **选择图表组件**（参考下方组件库）：根据内容选用合适的可视化模块组合
3. **生成 HTML**：按规范构造完整 HTML 文件，所有样式内联在 `<style>` 中
4. **自动保存**：使用 Write 工具保存到当前工作目录
5. **反馈用户**：告知文件路径和打开方式

## 文件命名规范

```
{主题}-{类型}.html
```

示例：
- `auth-login-flow.html`
- `order-processing-diagram.html`
- `request-pipeline-flow.html`
- `state-machine-diagram.html`

---

## 设计系统（Design System）

### CSS 变量（必须定义在 `:root`）

```css
:root {
  --blue-dark: #1e40af;
  --blue: #3b82f6;
  --blue-light: #dbeafe;
  --green-dark: #15803d;
  --green: #22c55e;
  --green-light: #dcfce7;
  --orange-dark: #c2410c;
  --orange: #f97316;
  --orange-light: #ffedd5;
  --purple-dark: #6b21a8;
  --purple: #a855f7;
  --purple-light: #f3e8ff;
  --red-dark: #b91c1c;
  --red: #ef4444;
  --red-light: #fee2e2;
  --gray-dark: #374151;
  --gray: #6b7280;
  --gray-light: #f9fafb;
  --border: #e5e7eb;
}
```

### 颜色语义

| 颜色 | 语义 | 典型用途 |
|------|------|---------|
| blue | 发起方、输入、信息 | 调用方角色、请求发起、入口模块 |
| green | 接收方、成功、已完成 | 处理完成、成功分支、输出结果 |
| orange | 外部系统、警告、中间件 | 第三方服务、中间件处理、告警 |
| purple | 抽象层、认证、核心逻辑 | 业务逻辑处理、Auth 阶段、框架层 |
| red | 错误、拒绝、终止 | 失败分支、异常处理、流程终止 |
| yellow/fef9c3 | 检测、决策、待定 | 条件判断、分支决策节点 |
| gray | 中性、底层、基础设施 | 基础设施层、空闲状态、辅助信息 |

---

## 组件库（Component Library）

### 1. 页面基础框架

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{标题}</title>
<style>
  /* 粘贴完整 CSS */
</style>
</head>
<body>
<div class="page">
  <div>
    <h1>{主标题}</h1>
    <p class="subtitle">{副标题，用 · 分隔各节名称}</p>
  </div>
  <!-- 各卡片 -->
</div>
</body>
</html>
```

**基础 CSS：**
```css
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'PingFang SC', 'Microsoft YaHei', sans-serif;
  background: #f1f5f9;
  color: var(--gray-dark);
  padding: 32px 24px;
  min-height: 100vh;
}
h1 { text-align: center; font-size: 22px; font-weight: 700; color: var(--blue-dark); margin-bottom: 6px; }
.subtitle { text-align: center; font-size: 13px; color: var(--gray); margin-bottom: 36px; }
.page { max-width: 1100px; margin: 0 auto; display: flex; flex-direction: column; gap: 36px; }
```

---

### 2. 卡片容器（Card）

每个主题区块用一个 card 包裹：

```html
<div class="card">
  <div class="card-title">{标题} <span class="badge">{英文副标题}</span></div>
  <!-- 内容 -->
</div>
```

```css
.card {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 1px 4px rgba(0,0,0,.08), 0 4px 16px rgba(0,0,0,.06);
  padding: 28px 32px;
}
.card-title {
  font-size: 15px; font-weight: 700; color: var(--blue-dark);
  margin-bottom: 24px; padding-bottom: 10px;
  border-bottom: 2px solid var(--blue-light);
  display: flex; align-items: center; gap: 8px;
}
.card-title .badge {
  font-size: 11px; font-weight: 600;
  background: var(--blue-light); color: var(--blue-dark);
  border-radius: 4px; padding: 2px 7px;
}
```

---

### 3. 角色栏（Actors / Roles）

展示流程中的参与方/模块/角色：

```html
<div class="roles">
  <div class="role role-client">调用方<div class="role-label">前端/客户端</div></div>
  <div class="role role-server">处理方<div class="role-label">后端服务</div></div>
  <div class="role role-third">外部系统<div class="role-label">第三方API</div></div>
</div>
```

```css
.roles { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 12px; margin-bottom: 28px; }
.role { border-radius: 8px; padding: 12px 14px; font-size: 12px; font-weight: 600; text-align: center; border: 1.5px solid transparent; }
.role .role-label { font-size: 10px; font-weight: 400; margin-top: 3px; opacity: .8; }
.role-client   { background: var(--blue-light);   color: var(--blue-dark);   border-color: #93c5fd; }
.role-server   { background: var(--green-light);  color: var(--green-dark);  border-color: #86efac; }
.role-third    { background: var(--orange-light); color: var(--orange-dark); border-color: #fdba74; }
.role-external { background: var(--purple-light); color: var(--purple-dark); border-color: #d8b4fe; }
```

---

### 4. 步骤流程（Numbered Flow）

带连接线的有序步骤，适合任何顺序执行的流程（如请求处理、函数调用链、算法步骤等）：

```html
<div class="flow">
  <div class="flow-step">
    <div class="step-num">
      <div class="step-circle">1</div>
      <div class="step-line"></div>   <!-- 最后一步不加 step-line -->
    </div>
    <div class="step-body">
      <div class="step-header">
        <span class="step-title">步骤标题</span>
        <span class="tag tag-client">客户端</span>
      </div>
      <div class="step-detail">
        步骤描述文字，可包含 <strong>强调</strong> 和列表。
        <ul><li>要点 1</li><li>要点 2</li></ul>
      </div>
    </div>
  </div>
  <!-- 更多步骤 -->
</div>
```

```css
.flow { display: flex; flex-direction: column; gap: 0; }
.flow-step { display: flex; gap: 0; position: relative; }
.step-num { width: 36px; flex-shrink: 0; display: flex; flex-direction: column; align-items: center; }
.step-circle {
  width: 28px; height: 28px; border-radius: 50%;
  background: var(--blue-dark); color: #fff;
  font-size: 12px; font-weight: 700;
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0; position: relative; z-index: 1;
}
.step-line { width: 2px; flex: 1; background: var(--border); margin-top: 2px; margin-bottom: 2px; min-height: 16px; }
.step-body { flex: 1; padding: 0 0 20px 16px; }
.step-header { display: flex; align-items: center; gap: 8px; margin-bottom: 6px; min-height: 28px; }
.step-title { font-size: 13px; font-weight: 700; color: var(--gray-dark); }
.step-detail { font-size: 12px; color: var(--gray); line-height: 1.7; }
.step-detail ul { padding-left: 16px; }
.step-detail li { margin-bottom: 2px; }
/* 标签 */
.tag { font-size: 10px; font-weight: 600; border-radius: 4px; padding: 2px 6px; }
.tag-client { background: var(--blue-light);  color: var(--blue-dark); }
.tag-server { background: var(--green-light); color: var(--green-dark); }
.tag-both   { background: #fef9c3; color: #854d0e; }
```

---

### 5. 分叉分支（Fork / Branch）

步骤内的条件分叉，如"匹配/不匹配"、"是/否"：

```html
<div class="fork">
  <div class="fork-branch accept">
    <div class="fork-label"><span class="dot dot-green"></span>条件成立</div>
    描述成功路径的处理逻辑。
  </div>
  <div class="fork-branch reject">
    <div class="fork-label"><span class="dot dot-red"></span>条件不成立</div>
    描述失败或回落路径。
  </div>
</div>
```

```css
.fork { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-top: 8px; }
.fork-branch { border-radius: 8px; padding: 12px 14px; font-size: 12px; border: 1.5px solid var(--border); }
.fork-branch .fork-label { font-size: 11px; font-weight: 700; margin-bottom: 4px; display: flex; align-items: center; gap: 5px; }
.fork-branch.pass   { border-color: #86efac; background: var(--green-light); }
.fork-branch.normal { border-color: #93c5fd; background: var(--blue-light); }
.fork-branch.reject { border-color: #fca5a5; background: var(--red-light); }
.fork-branch.accept { border-color: #86efac; background: var(--green-light); }
.dot { width: 8px; height: 8px; border-radius: 50%; display: inline-block; flex-shrink: 0; }
.dot-green { background: var(--green); }
.dot-blue  { background: var(--blue); }
.dot-red   { background: var(--red); }
```

---

### 6. 层次结构（Stack Layers）

展示分层架构（自上而下），适用于技术栈、调用层次、模块分层等：

```html
<div class="stack-wrap">
  <div class="stack-col">
    <div class="stack-label">前端</div>
    <div class="stack-layer sl-1"><span class="sl-name">UI 组件</span><span class="sl-detail">React / Vue</span></div>
    <div class="stack-layer sl-2"><span class="sl-name">状态管理</span><span class="sl-detail">Redux / Pinia</span></div>
    <div class="stack-layer sl-3"><span class="sl-name">API 层</span><span class="sl-detail">Axios / Fetch</span></div>
    <div class="stack-layer sl-4"><span class="sl-name">网络层</span><span class="sl-detail">HTTP / WebSocket</span></div>
    <div class="stack-layer sl-5"><span class="sl-name">传输层</span><span class="sl-detail">TCP / UDP</span></div>
  </div>
  <!-- 右侧对称列 -->
</div>
```

```css
.stack-wrap { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
.stack-col { display: flex; flex-direction: column; gap: 0; }
.stack-label { font-size: 12px; font-weight: 700; color: var(--gray); margin-bottom: 8px; text-align: center; text-transform: uppercase; letter-spacing: .05em; }
.stack-layer { border: 1.5px solid var(--border); border-bottom: none; padding: 10px 16px; font-size: 12px; display: flex; justify-content: space-between; align-items: center; }
.stack-layer:last-child { border-bottom: 1.5px solid var(--border); border-radius: 0 0 6px 6px; }
.stack-layer:first-child { border-radius: 6px 6px 0 0; }
.stack-layer .sl-name { font-weight: 600; }
.stack-layer .sl-detail { font-size: 10px; color: var(--gray); }
.sl-1 { background: #eff6ff; } .sl-2 { background: #f0fdf4; }
.sl-3 { background: #faf5ff; } .sl-4 { background: #fff7ed; }
.sl-5 { background: var(--gray-light); }
```

---

### 7. 数据结构条带（Field Strip）

展示数据结构的字段布局，适用于数据模型、消息格式、配置结构、API 请求/响应体等：

```html
<div class="pkt-row">
  <!-- fw-xs=52px  fw-s=80px  fw-m=120px  fw-l=180px  fw-xl=flex:1  fw-2xl=flex:2 -->
  <div class="pkt-field fw-xs fc-tcp">
    <span class="fn">字段名</span>
    <span class="fv">类型</span>
    <span class="fb">说明</span>
  </div>
  <div class="pkt-field fw-xl fc-tls">
    <span class="fn">内容区</span>
    <span class="fv">变长</span>
    <span class="fb">详细描述</span>
  </div>
  <!-- 高亮特殊字段用 fc-hl -->
  <div class="pkt-field fw-l fc-hl">
    <span class="fn">关键字段</span>
    <span class="fv">值</span>
    <span class="fb">重要说明</span>
  </div>
</div>
```

**字段背景色：**
```css
.fc-tcp     { background: #fff7ed; }   /* 基础层/底层 */
.fc-tls     { background: #eff6ff; }   /* 核心层/主要模块 */
.fc-reality { background: #f0fdf4; }   /* 辅助层/中间件 */
.fc-vless   { background: var(--purple-light); }  /* 业务逻辑层 */
.fc-vision  { background: #fef9c3; }   /* 决策/检测层 */
.fc-inner   { background: #f1f5f9; }   /* 内部数据 */
.fc-hl      { background: #fce7f3; }   /* 高亮/关键字段 */
.fc-data    { background: var(--gray-light); }    /* 通用数据 */
```

**完整 CSS：**
```css
.pkt-row { display: flex; border-radius: 6px; overflow: hidden; border: 1.5px solid var(--border); font-size: 11px; min-height: 38px; }
.pkt-field { display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 5px 8px; border-right: 1.5px solid var(--border); text-align: center; gap: 2px; }
.pkt-field:last-child { border-right: none; }
.pkt-field .fn { font-weight: 700; font-size: 11px; color: var(--gray-dark); }
.pkt-field .fv { font-size: 10px; color: var(--gray); font-family: 'SF Mono', 'Menlo', 'Consolas', monospace; }
.pkt-field .fb { font-size: 9px; color: var(--gray); opacity: .7; }
.fw-xs { flex: 0 0 52px; } .fw-s { flex: 0 0 80px; }
.fw-m  { flex: 0 0 120px; } .fw-l { flex: 0 0 180px; }
.fw-xl { flex: 1; min-width: 120px; } .fw-2xl { flex: 2; min-width: 160px; }
```

**嵌套展开子结构：**
```html
<div class="pkt-nested">
  <div class="pkt-nested-label">Extensions 展开</div>
  <div class="pkt-row"><!-- 子字段 --></div>
</div>
```
```css
.pkt-nested { margin-top: 6px; padding: 10px 12px; background: var(--gray-light); border-radius: 6px; border: 1.5px dashed var(--border); }
.pkt-nested-label { font-size: 10px; font-weight: 600; color: var(--gray); margin-bottom: 6px; }
```

---

### 8. 处理流程（Parse Flow）

展示逐层/逐步处理数据的过程，配合伪代码，适用于请求处理管线、数据转换、编译流程等：

```html
<div class="parse-flow">
  <div class="parse-step">
    <div class="parse-layer" style="background:var(--blue-light);color:var(--blue-dark);">验证层</div>
    <div class="parse-content">
      <div class="parse-action">动作标题</div>
      <div class="parse-detail">文字描述</div>
      <div class="parse-output">
        field = read(N)<br>
        <span class="key">if</span> condition: <span class="ok">→ 成功</span><br>
        <span class="key">else</span>: <span class="err">→ 失败</span>
      </div>
    </div>
  </div>
</div>
```

```css
.parse-flow { display: flex; flex-direction: column; gap: 0; }
.parse-step { display: flex; gap: 12px; padding: 10px 0; border-bottom: 1px solid var(--border); }
.parse-step:last-child { border-bottom: none; }
.parse-layer { width: 90px; flex-shrink: 0; font-size: 10px; font-weight: 700; padding: 4px 8px; border-radius: 4px; text-align: center; align-self: flex-start; margin-top: 2px; }
.parse-content { flex: 1; }
.parse-action { font-size: 12px; font-weight: 600; color: var(--gray-dark); margin-bottom: 3px; }
.parse-detail { font-size: 11px; color: var(--gray); line-height: 1.6; }
.parse-output { margin-top: 5px; font-size: 10px; font-family: 'SF Mono', 'Menlo', 'Consolas', monospace; background: #fff; border: 1px solid var(--border); border-radius: 4px; padding: 5px 8px; color: var(--gray-dark); line-height: 1.7; }
.parse-output .ok  { color: var(--green-dark); font-weight: 600; }
.parse-output .err { color: var(--red-dark);   font-weight: 600; }
.parse-output .key { color: var(--blue-dark);  font-weight: 600; }
```

---

### 9. 双列对比（Dual Column）

两个模块/角色/方案的并排对比：

```html
<div class="parse-dual">
  <div>
    <div class="parse-col-title pct-client">方案 A / 发起方</div>
    <!-- 内容 -->
  </div>
  <div>
    <div class="parse-col-title pct-server">方案 B / 接收方</div>
    <!-- 内容 -->
  </div>
</div>
```

```css
.parse-dual { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.parse-col-title { font-size: 11px; font-weight: 700; margin-bottom: 8px; padding: 5px 10px; border-radius: 5px; text-align: center; }
.pct-client { background: var(--blue-light);  color: var(--blue-dark); }
.pct-server { background: var(--green-light); color: var(--green-dark); }
```

---

### 10. 生命周期/状态机（Lifecycle）

横向状态条，带状态转移箭头，适用于任何有状态转换的场景（对象生命周期、订单状态流转、任务调度等）：

```html
<div class="lifecycle">
  <div class="lc-item"><div class="lc-node lc-idle">初始化<div class="lc-sub">等待</div></div></div>
  <div class="lc-arrow">→</div>
  <div class="lc-item"><div class="lc-node lc-tcp">处理中<div class="lc-sub">执行任务</div></div></div>
  <div class="lc-arrow">→</div>
  <!-- 更多状态 -->
  <div class="lc-item"><div class="lc-node lc-close">已结束<div class="lc-sub">清理资源</div></div></div>
</div>
<!-- 分支说明 -->
<div class="lc-branch-wrap">
  <div class="lc-branch">
    <div class="lb-title"><span class="dot dot-red"></span>异常路径说明</div>
    <div style="font-size:11px;color:var(--gray);line-height:1.6;">描述文字</div>
  </div>
</div>
```

**状态颜色（可根据语义自定义 style，类名仅为历史命名，可用于任意状态语义）：**
```css
.lifecycle { display: flex; align-items: stretch; gap: 0; overflow-x: auto; padding-bottom: 4px; }
.lc-item { display: flex; align-items: stretch; flex-shrink: 0; }
.lc-node { border-radius: 8px; padding: 12px 14px; font-size: 11px; font-weight: 600; text-align: center; min-width: 90px; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 3px; border: 1.5px solid transparent; }
.lc-node .lc-sub { font-size: 10px; font-weight: 400; opacity: .75; }
.lc-arrow { display: flex; align-items: center; padding: 0 4px; color: var(--gray); font-size: 16px; }
.lc-idle     { background: var(--gray-light);   color: var(--gray);        border-color: var(--border); }
.lc-tcp      { background: #fff7ed;             color: #9a3412;            border-color: #fdba74; }
.lc-tls      { background: var(--blue-light);   color: var(--blue-dark);   border-color: #93c5fd; }
.lc-auth     { background: var(--purple-light); color: var(--purple-dark); border-color: #d8b4fe; }
.lc-detect   { background: #fef9c3;             color: #854d0e;            border-color: #fde047; }
.lc-transfer { background: var(--green-light);  color: var(--green-dark);  border-color: #86efac; }
.lc-close    { background: var(--red-light);    color: var(--red-dark);    border-color: #fca5a5; }
.lc-branch-wrap { margin-top: 16px; display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 12px; }
.lc-branch { border-radius: 8px; padding: 12px 14px; font-size: 12px; border: 1.5px solid var(--border); }
.lc-branch .lb-title { font-size: 11px; font-weight: 700; margin-bottom: 6px; display: flex; align-items: center; gap: 5px; }
```

---

### 11. 数据流箭头（Data Flow Arrow）

展示数据/请求在各节点间的传输路径：

```html
<div class="df-row">
  <div class="df-node df-client">发起方<br><span style="font-size:10px;font-weight:400">模块说明</span></div>
  <div class="df-arrow">
    <div class="df-line df-pass-line" style="position:relative;">
      <span style="position:absolute;top:-15px;left:50%;transform:translateX(-50%);font-size:10px;color:var(--green-dark);white-space:nowrap;background:#fff;padding:1px 4px;border-radius:3px;">标签文字</span>
    </div>
  </div>
  <div class="df-node df-server">接收方</div>
</div>
```

```css
.df-row { display: flex; align-items: center; gap: 0; font-size: 12px; }
.df-node { border-radius: 6px; padding: 8px 12px; font-size: 11px; font-weight: 600; text-align: center; min-width: 80px; flex-shrink: 0; }
.df-arrow { flex: 1; display: flex; align-items: center; position: relative; padding: 0 4px; min-width: 60px; }
.df-line { flex: 1; height: 2px; position: relative; }
.df-line::after { content: ''; position: absolute; right: -1px; top: -4px; border: 5px solid transparent; border-left-color: inherit; }
.df-pass-line   { background: var(--green); } .df-pass-line::after   { border-left-color: var(--green); }
.df-normal-line { background: var(--blue); }  .df-normal-line::after { border-left-color: var(--blue); }
.df-reject-line { background: var(--red); }   .df-reject-line::after { border-left-color: var(--red); }
.df-client  { background: var(--blue-light);   color: var(--blue-dark); }
.df-server  { background: var(--green-light);  color: var(--green-dark); }
.df-hs      { background: var(--orange-light); color: var(--orange-dark); }
.df-target  { background: var(--purple-light); color: var(--purple-dark); }
```

---

### 12. 通用辅助

```css
/* 分隔线 */
.section-divider { height: 1px; background: var(--border); margin: 20px 0; }

/* 信息提示框 */
.info-box { font-size: 11px; color: var(--gray); background: var(--gray-light); border-radius: 6px; padding: 10px 14px; line-height: 1.7; }

/* 响应式 */
@media (max-width: 700px) {
  .roles { grid-template-columns: 1fr 1fr; }
  .fork  { grid-template-columns: 1fr; }
  .stack-wrap { grid-template-columns: 1fr; }
  .lc-branch-wrap { grid-template-columns: 1fr; }
  .lifecycle { flex-direction: column; align-items: flex-start; }
  .lc-arrow { transform: rotate(90deg); }
  .parse-dual { grid-template-columns: 1fr; }
  .pkt-row { flex-wrap: wrap; }
}
```

---

## 图表类型选择指南

| 内容类型 | 推荐组件组合 |
|---------|-------------|
| 代码执行流程 | 角色栏 + 步骤流程 + 分叉分支 |
| 请求处理管线 | 步骤流程 + 处理流程 + 分叉分支 |
| 数据模型/结构 | 数据结构条带 + 嵌套展开 + 处理流程 |
| 前后端交互 | 层次结构 + 双列对比 + 处理流程 |
| 数据流转路径 | 数据流箭头（多行） |
| 系统架构 | 角色栏 + 数据流箭头 + 分叉分支 |
| 状态机/生命周期 | 生命周期状态条 + 分支说明 |
| 算法步骤 | 步骤流程 + 分叉分支 + 处理流程 |

**复杂主题**可将多种类型组合在多个卡片中，灵活搭配。

---

## 输出规范

1. **完整 HTML**：一个独立文件，`<style>` 内联，无外部 CDN 依赖
2. **CSS 变量集中定义**：全部放在 `:root` 块，不散落在各处
3. **所有用到的组件 CSS 都必须包含**：按需从上方组件库复制，不引用外部
4. **不使用 Emoji**：纯文字 + 颜色区分，无表情符号
5. **保存路径**：使用 Write 工具保存到 `{当前工作目录}/{文件名}.html`

## 反馈格式

生成完成后告知用户：

```
HTML 图表已生成！

保存位置：{文件路径}

包含以下节：
- {节名 1}
- {节名 2}
- ...

用浏览器直接打开即可查看，无需安装任何依赖。
```
