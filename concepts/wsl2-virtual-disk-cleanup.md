---
title: WSL2 虚拟磁盘膨胀与清理
created: 2026-04-28
updated: 2026-04-28
type: concept
tags: [devops, methodology, tool]
sources: [raw/articles/wsl2-ghost-space-why-deleted-files-dont-free-disk.md]
confidence: high
---

# WSL2 虚拟磁盘膨胀与清理

WSL2 将 Linux 文件系统封装在一个 `.vhdx` 虚拟磁盘文件中。这个文件像气球一样容易膨胀，却不会自动收窄——删除 Linux 内部的文件只是在 "气球内部" 释放了空间，但 Windows 看到的 `.vhdx` 文件大小未变。

## 根本原因

- VHDx 是**固定大小的虚拟磁盘**，系统没有自动回收已删除区块的机制。
- Linux 的 `fstrim` 可以标记未使用空间，但需要 Windows 层的 `compact vdisk` 才能真正释放空间。

## 清理步骤

1. **Linux 内部标记**：
   ```bash
   sudo fstrim /
   ```

2. **关闭 WSL2**：
   ```bash
   wsl --shutdown
   ```

3. **Windows 层压缩**（管理员 PowerShell）：
   ```powershell
   diskpart
   select vdisk file="C:\Users\<User>\AppData\Local\Packages\<Distro>\LocalState\ext4.vhdx"
   attach vdisk readonly
   compact vdisk
   detach vdisk
   exit
   ```

## 预防

- 定期执行上述步骤。
- 在 `/etc/wsl.conf` 中配置 `[automount] options = "metadata"` 以改善文件系统行为。

## 参考

- 微信文章：WSL2中的幽灵空间 ^[raw/articles/wsl2-ghost-space-why-deleted-files-dont-free-disk.md]
- 相关实体：[[wsl2]]
