# Codex × Gemini 协作循环

让 Codex 与 Gemini 围绕同一份真实作品共同构思、修改和验证。适用于文字、方案、汇报、设计、代码与 skill 创作。

**对齐目标 → 创作 → Gemini 定向参与 → 核实取舍 → 修改 → 实际验证 → 交付或下一轮**。

用户决定目标和边界；Codex 负责实施、事实核对、取舍和交付；Gemini 根据当前瓶颈参与共同构思、首次试读、反例检查或直接改稿。判断依据是用户目标、证据和实际工具检查，模型之间相互认可不是完成标准。

## 使用

在 Codex 中调用：

> 请用 $codex-gemini-loop，和 Gemini 讨论着完善这个方案。先做出可审阅版本，让它检查目标读者能否理解，再核实意见、修改并验证后交付。

或用于技能创作：

> 用 $codex-gemini-loop 设计并实现一个新 skill。让 Gemini 参与结构设计、阅读实际初稿并提出具体修改；由你核实取舍、修改、校验后提交。

已认可的内容作为本轮基线，局部修改保留范围；实质问题解决后收敛，小修改不强制重复整套流程。

## 安装

可让 Codex 的 skill installer 安装本仓库根目录：

> 请安装 https://github.com/Biogod2020/codex-gemini-loop 这个 skill。

手动安装到尚未存在的技能目录：

```bash
git clone https://github.com/Biogod2020/codex-gemini-loop.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/codex-gemini-loop"
```

Gemini 调用使用宿主环境已有的工具或客户端。默认模型偏好是 Gemini 3.8 Flash high，当前用户指定优先；仓库不包含 API 凭证或私人路由。调用未完成时，如实标注，不把自审称为双模型协作。

## 文件

- [SKILL.md](SKILL.md)：完整循环、角色分工、取舍和结束条件。
- [交接提示](references/handoff-prompts.md)：共同构思、试读、改写、挑战和改后复核的提示模板。
- [实际创建示例](references/skill-creation-example.md)：本 skill 的三次真实协作交接，以及采纳和未采纳意见的理由。
- [agents/openai.yaml](agents/openai.yaml)：Codex 界面元信息。

这套方法提炼自一次研究图的持续协作，随后抽象成通用工作循环。创建 skill 本身也实际采用该循环；示例中的文本情景审阅不等同于所有应用领域的端到端验证。
