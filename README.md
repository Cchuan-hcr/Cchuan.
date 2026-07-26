# EPMA 数据转换器

用于将 EPMA 数据导入 AX-Win 进行阳离子分析处理前的 Windows 格式转换器。

## 功能

- **Excel 转 TXT**：将 EPMA Excel 数据转换为适合导入 AX-Win 的文本格式。
- **TXT 转 Excel**：将 AX-Win 输出的 `tab.txt` 文件转换回 Excel 格式，便于后续整理和分析。
- 转换完成后可先预览结果，再选择保存。

## 下载

建议从仓库的 [Releases](https://github.com/Cchuan-hcr/Cchuan./releases/latest) 页面下载最新版本：

- `EPMA.exe`（页面显示标签为“EPMA 数据转换器（Windows）”）

当前版本：`v1.0.0`

GitHub 会自动简化 Release 附件中的中文文件名。Release 中的 `EPMA.exe` 与仓库内的 `EPMA数据转换.exe` 内容相同。

## 使用方法

1. 从 Releases 页面下载 `EPMA.exe`。
2. 双击运行程序。
3. 选择“Excel 转 TXT”或“TXT 转 Excel”，然后选择需要转换的文件。
4. 点击“转换”，检查预览内容无误后点击“保存”。

使用“TXT 转 Excel”时，请选择 AX-Win 输出的 `tab.txt` 文件。

## 系统要求

- Windows 操作系统

## 文件校验

`v1.0.0` 版本的 SHA-256：

```text
0FB0DFAB6893EC081BCBC5AEB2D798DA50D4A3A6D112B2333FAB244C75203FFD  EPMA数据转换.exe
0FB0DFAB6893EC081BCBC5AEB2D798DA50D4A3A6D112B2333FAB244C75203FFD  EPMA.exe
```

仓库同时提供 `SHA256SUMS.txt`，可用于核对下载文件是否完整。

## Windows 安全提示

当前可执行文件尚未添加数字签名，因此 Windows SmartScreen 可能显示安全提醒。请确认下载来源为本仓库，并在运行前核对 SHA-256。

## 问题反馈

如遇到转换或使用问题，可以在本仓库的 [Issues](https://github.com/Cchuan-hcr/Cchuan./issues) 页面提交反馈。

## 许可证

本仓库暂未添加开源许可证。
