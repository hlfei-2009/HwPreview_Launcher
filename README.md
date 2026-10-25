# HwPreview_Launcher
一款 文件预览启动器 应用 (以下简称“此应用”)，包名为 com.hlfei.android.hwpreview_launcher，最低支持 Android 5。当您在某个应用 (如 MT管理器) 打开华为 文件预览 (com.huawei.hwpreview) 支持打开的文件时，此应用可辅助打开您华为设备上的 文件预览 应用以打开文件，从而解决因在打开方式选择器上不显示华为 文件预览 应用而导致无法通过其打开的问题。

MT管理器 打开方式选择器：
![IMG_20261025_082547.jpg](https://github.com/user-attachments/assets/59b11bb0-805a-4d24-8719-1e15bab6cf15)

Android 系统 打开方式选择器：
![IMG_20261025_083246.jpg](https://github.com/user-attachments/assets/e6d513a8-67db-458a-9553-f947c08a06a0)

# 工作原理是什么？
打开此应用后马上就会以带文件参数的显式 Intent (com.huawei.hwpreview/com.huawei.hwpreview.HwPreviewActivity) 打开华为 文件预览 应用，从而打开并预览文件。

# 为什么在打开方式选择器上不显示华为 文件预览 应用？
这是因为在华为 文件预览 应用的 AndroidManifest.xml 中有

meta-data
                android:name="ChooseDisabled"
                android:value="true" />

标签，并且应用于 com.huawei.hwpreview.HwPreviewActivity 活动。所以会不显示。

# 其他设备制造商的设备能使用此应用吗？
不能，因为只有华为设备自带 文件预览 (com.huawei.hwpreview) 应用，这个 文件预览 应用安装在其它设备制造商的设备上使用可是会闪退的。

# 支持打开什么格式的文件？
支持打开下列格式的文件 (xx/xx 表示 MIME 类型，.xx 表示文件格式)：

一、纯文本与网页

text/plain 纯文本文件（.txt、.log、无格式说明的文本）
text/html 网页文件（.html、.htm）
application/xhtml+xml XHTML 网页（.xhtml），HTML 的 XML 严格版

二、PDF

application/pdf PDF 文档（.pdf）

三、Word 文档

application/msword 旧版 Word 文档（.doc）
application/vnd.ms-word.document.macroEnabled.12 启用宏的 Word 文档（.docm）
application/vnd.ms-word.template.macroEnabled.12 启用宏的 Word 模板（.dotm）
application/vnd.openxmlformats-officedocument.wordprocessingml.template Word 模板（.dotx）
application/vnd.openxmlformats-officedocument.wordprocessingml.document 新版 Word 文档（.docx）

四、Excel 表格

application/vnd.ms-excel 旧版 Excel 表格（.xls）
application/vnd.ms-excel.addin.macroenabled.12 启用宏的 Excel 加载项（.xlam）
application/vnd.ms-excel.sheet.binary.macroenabled.12 二进制工作簿（.xlsb）
application/vnd.ms-excel.sheet.macroEnabled.12 启用宏的 Excel 表格（.xlsm）
application/vnd.ms-excel.template.macroEnabled.12 启用宏的 Excel 模板（.xltm）
application/vnd.openxmlformats-officedocument.spreadsheetml.sheet 新版 Excel 表格（.xlsx）
application/vnd.openxmlformats-officedocument.spreadsheetml.template Excel 模板（.xltx）

五、PowerPoint 演示文稿

application/vnd.ms-powerpoint 旧版 PPT 演示文稿（.ppt）
application/vnd.ms-powerpoint.template.macroEnabled.12 启用宏的 PPT 模板（.potm）
application/vnd.openxmlformats-officedocument.presentationml.template PPT 模板（.potx）
application/vnd.ms-powerpoint.addin.macroenabled.12 启用宏的 PPT 加载项（.ppam）
application/vnd.ms-powerpoint.slideshow.macroEnabled.12 启用宏的 PPT 放映文件（.ppsm）
application/vnd.openxmlformats-officedocument.presentationml.slideshow PPT 放映文件（.ppsx）
application/vnd.ms-powerpoint.presentation.macroEnabled.12 启用宏的 PPT 演示文稿（.pptm）
application/vnd.openxmlformats-officedocument.presentationml.presentation 新版 PPT 演示文稿（.pptx）

六、图片

image/jpeg JPEG 图片（.jpg、.jpeg）
image/gif GIF 图片（.gif）
image/png PNG 图片（.png）
image/x-ms-bmp Windows 位图（.bmp）
image/vnd.wap.wbmp 无线应用协议位图（.wbmp），早期手机图片格式
image/webp WebP 图片（.webp），Google 推出的高压缩比格式

七、音频与视频（通配类型）

audio/* 所有音频文件（如 .mp3、.wav、.aac 等，具体格式由子类型或扩展名决定）
video/* 所有视频文件（如 .mp4、.mkv、.avi 等）
application/ogg / application/x-ogg Ogg 容器文件（.ogg），可容纳音频、视频、字幕
application/x-flac FLAC 无损音频（.flac）
application/itunes 苹果 iTunes 相关文件（如 .itlp 播放列表、.ipa 安装包等生态内文件）

上述这些格式都是从华为 文件预览 应用抄过来的，以确保此应用与华为 文件预览 应用支持打开的文件格式一致，否则我开发此应用将没什么用。
