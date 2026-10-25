# workbuddy.md — WorkBuddy 开发对话上下文

> 本项目（麦麦带娃点单安抚助手 / mcd-kids-order-peacemaker）全程在腾讯 WorkBuddy 智能体中开发，开发者为一位幼儿园男教师（非职业程序员），从创意构思、方案确认到全部文件编写均通过 WorkBuddy 对话完成。本文档为开发过程的对话上下文记录，用于 WorkBuddy 专项奖励核验。

## 开发环境

- 开发工具：腾讯 WorkBuddy 智能体（PC 端）
- 开发时间：2026 年 10 月 25 日 13:47 起（麦当劳程序员创意开发大赛报名截止日）
- 开发者背景：幼儿园教师，带大班，无职业编程经验

## 对话过程实录（摘要）

### 第 1 轮：了解赛事与寻找创意

**开发者**：（分享活动页链接）我想参加这个活动，没有啥灵感。

**WorkBuddy**：解析活动页（页面为动态加载，转由检索赛事官方 GitHub 仓库 M-China/mcd-developer-innovation-challenge 获取规则原文）。汇报关键信息：报名截止 2026-10-25 23:59（当天）、按 GitHub Star 排名、需提交 5 个标准文件、WorkBuddy 专项奖励需附 workbuddy.md。结合开发者职业背景（幼儿园教师、日常处理家长沟通与幼儿膳食）提出三个差异化创意方向，指出榜单前 100 名项目集中在"省钱比价"和"营养计算"，**家长沟通视角无人做**：
1. 麦麦带娃点单安抚助手（推荐）——输入孩子年龄+预算，输出三档清单+孩子听得懂的解释；
2. 麦麦亲子营养把关员——儿童营养师视角点评与改良；
3. 麦麦家庭日规划师——多人预算组合套餐。

**开发者**：没有 GitHub 账号，怎么注册？

**WorkBuddy**：给出注册步骤（github.com/signup、邮箱验证、用户名建议）。

### 第 2 轮：网络问题排查

**开发者**：（截图）注册了打不开啊。（Edge 显示 github.com 响应时间过长）

**WorkBuddy**：在本机实测诊断：`api.github.com`、`raw.githubusercontent.com`、`codeload.github.com` 均连通（1.2s 内），仅 `github.com` 主站对 4 个 IP 全部超时——典型的主站域名级阻断。给出三级方案：①手机流量注册（最快）；②微软商店安装 Watt Toolkit 做 GitHub 加速；③代理全局。并告知：注册完成后，建仓库、传文件、提交 Issue 均可通过已连通的 `api.github.com` 接口代为完成。

### 第 3 轮：创意确认与项目启动

**开发者**：可以了（已注册账号、已领取麦当劳 MCP Token）。同时通过选项确认采用创意 1「带娃点单安抚助手」。

**WorkBuddy**：通过 `api.github.com` 拉取赛事官方规则（activityGuidelines.md、CONTEST_DECLARATION.md 原文）与麦当劳 MCP Server 使用指南（M-China/mcd-mcp-server，33 个 Tool 清单），确认：
- 5 个参赛文件的硬性要求与 Issue 报名模板；
- 设计决策：遵循**最小权限原则**，Skill 只使用只读与试算类工具（now-time-info / query-meals / list-nutrition-foods / query-my-coupons / query-my-account / calculate-price / query-meal-detail / query-nearby-stores 等），不调用 create-order 等写操作工具，支付责任留在用户手上；
- 完成 Skill 本体（SKILL.md + 儿童营养参考线 + 亲子沟通话术库两个 references）与全部参赛文件编写。

## 本项目的 WorkBuddy 特色

1. **真实使用 WorkBuddy 智能体**：从活动解读、网络诊断、规则抓取到代码与文档产出，全流程单一会话内完成，开发者全程只做决策与验收；
2. **职业背景注入**：儿童营养参考线整理自公开膳食指南，亲子话术库来自开发者的幼儿园一线带班经验（分龄话术、禁用语红线、情绪急救三条），这是通用大模型默认风格给不出的内容；
3. **安全设计**：Skill 强制只读工具白名单，符合"Agent 建单、人来付款"的消费级 Agent 责任边界。

## 声明

以上对话过程真实发生，对话原始记录保留于开发者的 WorkBuddy 账户中，可供核验。
