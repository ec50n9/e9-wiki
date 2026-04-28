---
source_url: https://mp.weixin.qq.com/s/z0_XlPDasrDTotz62_GHCg
ingested: 2026-04-28
sha256: a5d83806efa95b89254c1b53919330196d8e3ee98093d8ed9a209567e55cad67
---

# WSL2中的幽灵空间：为什么删除文件后磁盘空间不变？

你是否曾在WSL2中删除了一个巨型文件，期待释放大量空间，却发现磁盘使用量纹丝不动？别担心，你不是一个人！让我们一起揭开这个谜团，并学习如何真正"驱除"这些幽灵空间。🚀

🤔 问题的根源

WSL2的虚拟磁盘机制 📦

WSL2使用虚拟硬盘(VHD)文件来存储整个Linux文件系统。

这个VHD文件就像一个不断膨胀的气球🎈，很容易变大，但不会自动缩小。

删除≠收缩 ✂️

在WSL2中删除文件时，只是在气球内部腾出了空间。

但对Windows来说，这个"气球"（VHD文件）的大小并没有变化。

💡 解决方案

1. WSL2内部清理 🧹

首先，我们需要告诉WSL2清理那些未使用的空间：

sudo fstrim /

这个命令就像是在气球内部进行大扫除，把所有不用的"垃圾"都集中到一起。

2. 从Windows角度缩小VHD 🗜️

接下来，我们需要从Windows的角度来真正缩小这个"气球"：

关闭所有WSL实例：

wsl --shutdown

运行diskpart命令（需要管理员权限的PowerShell）：

diskpart
select vdisk file="C:\Users\[YourUsername]\AppData\Local\Packages\[WSLDistro]\LocalState\ext4.vhdx"
attach vdisk readonly
compact vdisk
detach vdisk
exit

这个过程就像是给气球打气筒，但是反着用，把里面多余的空气抽出来。😮‍💨

🛡️ 预防措施

定期清理 🗓️

把上述步骤加入你的日程安排，比如每月一次。

启用case sensitivity 🔠

在/etc/wsl.conf中添加：

[automount]
options = "metadata"

这可以帮助更好地管理文件系统，就像给你的文件柜装了个更智能的文件分类系统。

🎉 结语

通过以上步骤，你应该能够成功"驱魔"，让你的WSL2恢复苗条身材。记住，磁盘管理就像园艺🌱 —— 需要定期修剪和维护，才能保持健康和高效。

下次当你的同事抱怨WSL2占用了太多空间时，你就能像一个真正的魔法师一样，挥挥手让那些"幽灵空间"消失不见了！💼✨

以上。
