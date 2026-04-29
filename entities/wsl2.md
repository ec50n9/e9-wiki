---
title: WSL2
created: 2026-04-28
updated: 2026-04-28
type: entity
tags: [devops, tool]
sources: [raw/articles/wsl2-ghost-space-why-deleted-files-dont-free-disk.md]
confidence: high
---

# WSL2

Windows Subsystem for Linux 2，微软提供的 Linux 兼容层，让 Windows 用户无需虚拟机即可运行原生 Linux 应用。

## 核心机制

与 WSL1 不同，WSL2 基于轻量级虚拟机，内部运行完整的 Linux 内核。文件系统存储在一个扩展名为 `.vhdx` 的虚拟硬盘文件中，通常位于 `AppData\Local\Packages\{Distro}\LocalState\ext4.vhdx`。

## 已知问题

- **VHD 膨胀**：由于虚拟磁盘文件不会自动收窄，删除文件后 Windows 层面的磁盘占用不会减少。见 [[wsl2-virtual-disk-cleanup]]。
- **性能**：跨文件系统边界（Windows 与 Linux 之间）的 IO 性能低于纯 Linux 环境。

## 参考

- 微信文章：WSL2中的幽灵空间 ^[raw/articles/wsl2-ghost-space-why-deleted-files-dont-free-disk.md]
