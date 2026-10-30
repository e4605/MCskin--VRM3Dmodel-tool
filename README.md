# MC Skin → VRM 1.1

把 Minecraft 皮肤转换为带骨骼的 VRM 0.x 模型，同时输出可编辑的 Blender 工程。支持 Windows x64，需要本机安装 Blender 5.2。

## 下载

- **[下载 Windows 完整工具包](https://github.com/e4605/MCskin--VRM3Dmodel-tool/raw/refs/heads/main/MCSkinVRM-v1.1.0-Windows-x64.zip)**
- [下载完整源码](https://github.com/e4605/MCskin--VRM3Dmodel-tool/raw/refs/heads/main/MCSkinVRM-v1.1.0-Source.zip)
- [SHA-256 校验文件](SHA256SUMS.txt)

完整解压 Windows 工具包后，运行 `MCSkinVRM.exe`。必须保留同目录的 `_internal` 文件夹。请使用上面的完整包下载链接；单独的 EXE 缺少运行依赖。

## 快速使用

1. 选择 MC 皮肤 PNG，确认普通手臂（Steve）或细手臂（Alex）。
2. 点击“自动查找”，或选择 Blender 5.2 安装文件夹里的 `blender.exe`。这里需要程序文件路径，无需输入版本号。
3. 需要眨眼时，点击“配置眼睛像素”，按①②标记画面右侧、左侧的眼睛；选中格子显示 √。qwq 示例可点击“一键示范”，再点击“应用并启用眨眼”。
4. 点击“开始转换”，完成后打开输出目录，获取 `Avatar.vrm`、`Avatar.blend` 和可选的 `preview.png`。

## 功能与使用范围

Windows 本地 MC 皮肤转 VRM 工具。启动与使用见 [使用说明](使用说明.md)，研究来源和验证边界见 [研究与兼容性](研究与兼容性.md)。

- 中文桌面界面，导入皮肤并输出 VRM 0.x、打包贴图的 Blender 工程和可选预览图。
- Steve / Alex、旧版镜像补全、64 / 128 / 256 宽皮肤、透明第二层。
- 不新增嘴巴或口型。可手动选眼睛制作眨眼与视线。
- 51 项人形骨骼映射，含双手手指。每次导出检查实际文件并重新导入验证。
- 使用本机 Blender 5.2；发布包自带界面依赖与 VRM 插件，无需另装 Python。

模型带手臂、肘部和手腕骨骼，可在 Blender 或支持相应骨骼驱动的软件中制作动作。保留 MC 方块手；附加的手指骨骼用于结构兼容，不提供独立五指蒙皮或实时手部追踪。

已根据此前排查加入直播姬手指骨骼兼容处理，并检查导出结构与 Blender 重新导入结果。**直播姬内实际加载与推流尚未验证，不承诺所有版本可直接导入。**

## 源码

下载源码 ZIP 并完整解压后，可查看 `app.py`、`cli.py`、`mcvrm`、Blender 后端及附带的 VRM 插件源码。源码安装方式和测试命令见使用说明。

源代码入口为 `app.py`；批处理可使用 `cli.py`。详见中文说明中的命令行和测试命令。

原始工具代码为 MIT 许可；第三方软件和用户提供的示例皮肤分别适用自身授权，见 [第三方说明](THIRD_PARTY_NOTICES.md)。
