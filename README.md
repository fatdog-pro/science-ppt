[README.md](https://github.com/user-attachments/files/33319690/README.md)
作者：抖音 萌猪过河

# science-ppt

根据主题、论文和研究材料制作原生可编辑的科研风格 PPT，适用于技术路线、机制图、实验流程、装置示意及组会、答辩汇报。普通主题和内置示例均默认在独立 WPS 新窗口中逐页、逐对象可见绘制，完成后保存并保持文稿打开。

## 在豆包中使用

先加载本技能，并确认豆包能够执行本地程序，或已启用配套本地 STDIO 连接器。技能加载与连接器配置是两件事；连接方法见 [豆包连接器](references/doubao-connector.md)。旧对话沿用旧流程时，让智能体重新读取 [SKILL.md](SKILL.md)。

普通主题可以这样请求：

> 使用 science-ppt，制作主题为“你的科研主题”的十页科研风格 PPT。在独立 WPS 新窗口中展示完整绘制过程，不加演示停顿，不主动最大化或抢占前台。

智能体根据材料设计本次完整场景，然后执行通用入口。页数、语言和版式服从本次需求；普通主题不会借用固定示例的内容。执行说明见 [通用可见绘制流程](references/ordinary-visible-workflow.md)。

## 完整重跑两个内置示例

单页“多模态传感与智能诊断技术路线”：

> 使用 science-ppt，完整重跑“多模态传感与智能诊断技术路线”单页示例，保持原构图、文字和配色，在独立 WPS 新窗口中逐项绘制，不加停顿，不主动最大化或抢占前台。

十页“芯片封装的发展历程”：

> 使用 science-ppt，完整重跑“芯片封装的发展历程”十页示例，保持原页序、构图、文字和配色，在独立 WPS 新窗口中逐项绘制，不加停顿，不主动最大化或抢占前台。

示例包含完整程序、固定场景和说明，每次在新的任务目录中重新生成。详细入口见 [单页多模态传感示例](references/multimodal-route-example.md) 和 [十页芯片封装示例](references/chip-packaging-history-example.md)。

## 本地环境与程序入口

完整可见绘制需要 Windows、已安装并注册 COM 的 WPS 演示，以及能加载 `pywin32` 的 Python 3.10+。环境检查和迁移说明见 [运行环境](references/environment.md)。

普通任务的本地命令如下，各占位路径替换为本机真实绝对路径，任务输出目录必须全新：

```text
python "<skill-root>/scripts/run_science_ppt.py" --scene "<absolute-scene.json>" --out-dir "<new-job-directory>" --wps-python "<absolute-python-with-pywin32>"
```

连接器的普通任务入口是 `export_scene`，默认执行完整 WPS 绘制流程。两个固定示例分别使用 `run_multimodal_route_example` 和 `run_chip_packaging_history_example`。

## 可见绘制与交付规则

- 先确认独立 WPS 空白文稿，再逐页、逐对象构建；只打开已做好的 PPT 或生成预览不能替代绘制过程。
- 尊重用户调整的窗口大小、位置、最小化状态和应用切换。翻页及结束时不强制激活、最大化或抢回焦点。
- 以应用允许的速度执行，不添加人工演示停顿；仅等待应用、剪贴板或保存就绪。
- 默认最终稿为 `science-visible.pptx`；内部源稿为 `figure-editable.pptx`。可见过程未完成时如实报告未完成项，不把源稿冒充完整流程的成品。
- 只有用户明确要求仅导出或不启动 WPS 时，才使用 `--export-only` / `"export_only":true`。
- 技能包仅保留程序、场景资料和说明，不包含成品 PPT 或预览图；生成结果与质量报告写入本次任务目录。

科学设计、对象格式和验收要求以 [SKILL.md](SKILL.md) 及其关联说明为准。
