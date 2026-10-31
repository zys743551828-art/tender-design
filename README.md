> 后续开发使用 `dev` 并跟踪 `origin/dev`；原 fusion/handoff 分支保留为来源。下列交接分支要求属于历史记录。

> Historical handoff: [HANDOFF-20261017.md](HANDOFF-20261017.md) records the former branch and scope. Continue on `dev`; use the [current installation and operation manual](https://github.com/zys743551828-art/tender-docs/blob/dev/使用说明.md) for the delivered workbench.

# tender-design

施组工作台既有实现的界面设计稿：十个可直接在浏览器中打开的静态页面，使用虚构的项目与数据（以“广德市污水管网改造及新建工程”为主线，各页数字一致）。

目标产品采用GovDash式项目工作区、章节编制、随页助手和版本导出，目标规范及布局示意见[交互与视觉设计](https://github.com/zys743551828-art/tender-docs/blob/dev/05-技术与设计/交互与视觉设计.md)。本仓库十个HTML页面保存既有基线，尚未按目标重做。

既有信息架构：全局为项目与度量；项目内导航依次为报告（落地页）、问题、依据、报价、提交与结果、资料，工具为检索与设置。系统只有登录一道门，不区分岗位，所有成员看到的是同一套页面。

视觉：中性灰底与单一松绿强调色，Inter 与思源黑体，数字等宽；衬线体只用于引用的原文。浅色侧栏带“搜索或跳转（Ctrl K）”入口；卡片 8 px 圆角、只用细线不加阴影，阴影只给对话框等浮层；控件 36 px 高、6 px 圆角；标签无边框浅底，只在状态需要醒目时使用。危险、警示、通过与 AI 建议各有一组浅底／文字／描边色。系统设为深色时页面自动切换为深色主题。

| 页面 | 内容 |
| --- | --- |
| [index.html](index.html) | 项目：一行一个项目，给出否决风险、预计技术分（含覆盖程度）、状态和与报告同源的下一步；新建项目只要求名称 |
| [report.html](report.html) | 评审报告：一句话结论与关键数字、下一步（按钮写明动作）、逐条响应（默认只展开需要处理的行）、技术分预测、全部问题、导出 |
| [findings.html](findings.html) | 问题：分类标签页、列表、详情（招标文件要求与施组正文写法并排）、处理动作与改稿建议 |
| [rules.html](rules.html) | 依据：规则分组，“全部按原文确认”一次确认待核对的规则，技术分满分与评标价规则的原文出处；事实库标签 |
| [price.html](price.html) | 报价：按招标文件原文填好的评标价规则（带出处）、竞争对手报价、候选报价、实时试算（结果表、价格分曲线、换算句、风险提示）、保存过的方案 |
| [submit.html](submit.html) | 提交与结果：登记前的检查逐项列出并给出处理入口，通过后才出现登记表单；登记开标结果 |
| [metrics.html](metrics.html) | 度量：入围率与中标率、废标／否决风险闭环、预测校准、逐轮得分趋势 |
| [materials.html](materials.html) | 资料：一次拖入多份文件，按文件名猜用途与版本、上传前可逐个改；版本与解析状态；顶部流水线进度 |
| [settings.html](settings.html) | 项目设置：项目信息与功能开关（自动开始评审、规则按原文接受、两类检测、显示预测分数、报价模块、提示登记开标结果），核心能力无开关 |
| [pipeline.html](pipeline.html) | 流水线状态：评审中断与重试、评审进行中、资料更新提示、等待手动开始、资料待补充、报告尚未生成 |

[styles.css](styles.css) 为各页共用的令牌（浅色与深色两套，与 tender-app 前端的设计令牌一致）与组件样式。`screenshots/` 为各页在 1440 像素宽度下的渲染图。页面不需要构建依赖；字体以固定 Fontsource 包自托管，离线也可加载三字体，来源与许可见 [本地字体说明](assets/fonts/README.md)；报价页、问题页等的交互使用少量内联脚本。

页面规范（信息架构、交互、视觉与可访问性）见 [tender-docs 的交互与视觉设计](https://github.com/zys743551828-art/tender-docs/blob/dev/05-技术与设计/交互与视觉设计.md)；实现见 [tender-app/workbench/apps/web](https://github.com/zys743551828-art/tender-app/tree/dev/workbench/apps/web)。
