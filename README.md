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
<meta-data
                android:name="ChooseDisabled"
                android:value="true" />
标签，并且应用于 com.huawei.hwpreview.HwPreviewActivity 活动。所以会不显示。

# 其他设备制造商的设备能使用此应用吗？
不能，因为只有华为设备自带 文件预览 (com.huawei.hwpreview) 应用，这个 文件预览 应用安装在其它设备制造商的设备上使用可是会闪退的。