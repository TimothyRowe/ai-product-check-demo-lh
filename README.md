# ai-product-check-demo-lh

产品库日常需求交互原型仓库，GitHub Pages 静态部署。

## 访问地址

- 导航首页：https://timothyrowe.github.io/ai-product-check-demo-lh/
- GitHub：https://github.com/TimothyRowe/ai-product-check-demo-lh.git

## 项目结构

```
├── index.html                    # 导航入口（所有Demo卡片）
├── customs-link-tool-demo.html   # 竞品检索工具 Demo
├── pda-sample-demo.html          # PDA 样品扫描优化 Demo
├── ai-check-demo.html            # 开品资料 AI 检测弹窗 Demo
├── ai-check-log-demo.html        # AI 检测日志 Demo
├── ai-config-demo.html           # AI 应用配置 Demo
└── README.md                     # 本文件
```

## 分支策略

- 仅使用 `main` 分支，直接 push 部署
- GitHub Pages 配置：Settings → Pages → Source: main / root

## 需求清单与飞书文档

| 需求 | Demo文件 | 飞书PRD | 状态 |
|------|----------|---------|------|
| 竞品检索工具 | customs-link-tool-demo.html | [PRD文档](https://my.feishu.cn/wiki/UgP1w48kfi0WaYkUoqLcd6aEnKf) | Demo+PRD完成 |
| PDA样品扫描优化 | pda-sample-demo.html | [需求初稿](https://my.feishu.cn/wiki/PZfxwbn3UiJYnUki2HvcdMNlnZf) | Demo完成，PRD已人工完善 |
| 开品资料AI检测 | ai-check-demo.html | — | Demo完成 |
| AI检测日志 | ai-check-log-demo.html | — | Demo完成 |
| AI应用配置 | ai-config-demo.html | — | Demo完成 |

## 竞品检索工具 — 核心设计

**功能定位**：产品库-工具箱，以图搜图匹配竞品ASIN销售链接，解决关务报关销售链接缺失问题。

**技术方案**：
- 数据源：Sorftime SimilarProductRealtimeRequest API（异步，约5分钟返回）
- 输入：SKU编码（批量≤100个）+ 目的国（单选）+ 平台（默认Amazon）
- 输出：每SKU取价格最低前3条竞品链接
- 推送：覆盖清关基础信息的销售链接字段，记录推送日志

**页面结构**：
- Tab1 检索工作台：输入→进度→结果表格（按SKU分组，最低价高亮）→推送清关
- Tab2 检索日志：筛选+历史列表+详情弹窗

**权限**：推送按钮仅关务专员+产品开发可操作

**2期规划**：导入检索（Excel模板：SKU+国家）、扩展为选品系统竞品筛选组件

## PDA 样品扫描优化 — 核心设计

**功能定位**：PDA扫码样品标签后，结果页增加状态可视化引导。

**状态流转**：来样确认 → 质检 → 拍照 → 入库/退货

**关键交互**：
- 状态指引横幅：告知仓库人员下一步送往哪个工作台
- 进度条：节点可视化（已完成/当前/未完成）
- 来源区分：新品开发（全节点）vs 老品变更（动态节点）
- 扫码支持物流单号（条形码/二维码）匹配样品需求单

## 关联项目

| 项目 | 仓库 | 用途 |
|------|------|------|
| 数字化选品系统 | [ai-selection-demo-lh](https://github.com/TimothyRowe/ai-selection-demo-lh) (私有) | 独立大项目，5模块Demo |
| AI技能共享平台 | [kte-skills-share-lh](https://github.com/TimothyRowe/kte-skills-share-lh) | 内部Skill平台Demo |
| 本仓库 | ai-product-check-demo-lh | 日常需求原型统一部署 |

## 开发约定

1. 所有Demo为纯静态HTML（数据硬编码，无需后端）
2. 新需求：创建 `xxx-demo.html` → 更新 `index.html` 导航卡片 → push main
3. 命名规范：`{功能}-demo.html`，小写中划线
4. PRD输出到飞书知识库对应节点，Demo文件内底部可加标注面板

## 本地开发

```bash
git clone https://github.com/TimothyRowe/ai-product-check-demo-lh.git
cd ai-product-check-demo-lh
# 直接双击html文件或起本地服务
npx serve .
```
