# MC Skin → VRM 1.2.0

将 Minecraft 皮肤转换为带骨骼的 VRM 0.x 模型，同时输出可编辑的 Blender 工程。**Windows x64，本地运行，不新增嘴巴。**

## 下载与启动

- **[下载 Windows 完整工具包](https://github.com/e4605/MCskin--VRM3Dmodel-tool/raw/refs/heads/main/MCSkinVRM-v1.2.0-Windows-x64.zip)**
- [下载完整源码](https://github.com/e4605/MCskin--VRM3Dmodel-tool/raw/refs/heads/main/MCSkinVRM-v1.2.0-Source.zip)
- [SHA-256 校验文件](SHA256SUMS.txt) · [更新记录](CHANGELOG.md) · [使用说明](使用说明.md)

完整解压工具包，保留同目录的 `_internal` 文件夹，再运行 `MCSkinVRM.exe`。便携包包含界面和插件依赖，无需另装 Python；本机仍需安装 Blender。

## Blender 多版本适配

支持 **Blender 4.2—5.2**。界面会检测程序的实际版本；通过“自动查找”填写路径，或在“高级选项 → Blender 检测”查看和切换版本。

| 已实测版本 | 骨骼与像素检查 | 导出与重新导入 | 工程挥手动作 |
| --- | --- | --- | --- |
| 4.2.23 LTS | 通过 | 通过 | 通过 |
| 4.5.15 LTS | 通过 | 通过 | 通过 |
| 5.2.3 LTS | 通过 | 通过 | 通过 |

三个版本共完成 12 项实际转换，覆盖细手臂及眼睛表情、普通手臂、旧版、高清皮肤。区间内其他小版本未逐一测试；详见 [兼容测试记录](compatibility.json) 和 [研究依据](研究与兼容性.md)。

## 普通转换

1. 选择皮肤 PNG，确认普通／细手臂。
2. 点击“自动查找”，或选中安装文件夹里的 `blender.exe`；不需要输入版本号。
3. 选择输出目录。遇到拒绝访问可点“推荐目录”，程序也会尝试其他可写目录并显示实际位置。
4. 点击“开始转换”，完成后打开输出目录获取 `Avatar.vrm`、`Avatar.blend` 和预览图。

需要眨眼时，先点击“配置眼睛像素”，按画面左、右侧分别点选；所选格子显示 √。只有匹配 qwq 正脸时才启用一键示范，避免把示例坐标套到其他皮肤上。

## 高级选项

主界面只保留常用操作；以下功能集中放在独立的“高级选项”窗口：

- **批量转换**：选择多张 PNG 或一个文件夹，逐个建模；单张失败继续处理，输出结果报告，支持取消。每批最多 200 张，默认静态脸。
- **预览质量**：快速 512×640、标准 800×1000、高清 1024×1280。
- **三视图**：额外输出正面、侧面、背面 PNG。
- **挥手演示**：通过真实手臂、肘部、手腕骨骼生成动作，保存在 Blender 工程中；VRM 保持标准静止姿态。
- **导出选择**：保留工程或仅导出 VRM。
- **更多设置**：作者、身高、不透明外层处理、单次超时、Blender 扫描与版本切换。

## 格式与边界

支持 Steve / Alex、64 / 128 / 256 像素宽 PNG、对应旧版 2:1 格式、透明第二层。高清子像素保留，使用最近邻纹理。模型保留 MC 方块手，附加手指骨骼用于结构兼容，不提供独立五指蒙皮或实时手部追踪。

不新增嘴部几何或口型；原皮肤画有嘴巴时会保留原像素。已加入此前排查得到的直播姬手指骨骼兼容处理，**直播姬实际加载与推流尚未验证**，不能替代目标软件实测。

## 源码与验证

完整解压源码 ZIP，入口为 `app.py` 和 `cli.py`。安装 `requirements.txt` 后可运行界面或命令行；构建便携版还需 `requirements-build.txt`。

```powershell
python app.py
python cli.py skin.png --output exports --blender "D:\Blender\blender.exe"
python cli.py --batch skins --output exports --no-preview --no-blend
python cli.py skin.png --output exports --views --wave-demo
python -m unittest discover -s tests -p "test_*.py" -v
```

原始工具代码采用 MIT 许可，第三方组件与示例皮肤适用各自授权，见 [第三方说明](THIRD_PARTY_NOTICES.md)。
