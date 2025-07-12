---
title: adb-scrcpy
published: 2024-01-30T11:47:36+08:00
summary: "利用adb的系统级控制"
cover:
  image: "https://rba.kanostar.top/adapt"
tags: [ADB]
categories: 'ADB'
draft: false 
lang: ''
---

> 使用前先用adb连接上设备

# 使用

默认

```bash
scrcpy
```

推荐使用这条

```bash
scrcpy -m 1024 -b 2M --max-fps 30
```

| 操作                                 | 快捷键                   |
| ------------------------------------ | ------------------------ |
| 切换全屏模式                         | MOD+f                    |
| 向左旋转显示                         | MOD+←（向左）            |
| 向右旋转显示                         | MOD+→（右）              |
| 将窗口大小调整为 1:1（像素完美）     | MOD+g                    |
| 调整窗口大小以去除黑边               | MOD+w \| 双击左键        |
| 点击 HOME                            | MOD+h \| 中键单击        |
| 点击返回                             | MOD+b \| 右键单击        |
| 点击APP_SWITCH                       | MOD+s  \| 第四次点击     |
| 点击MENU（解锁屏幕）                 | MOD+m                    |
| 点击VOLUME_UP                        | MOD+↑（向上）            |
| 点击VOLUME_DOWN                      | MOD+↓（向下）            |
| 点击 POWER                           | MOD+p                    |
| 开机                                 | 右击                     |
| 关闭设备屏幕（保持镜像）             | MOD+o                    |
| 打开设备屏幕                         | MOD+Shift+o              |
| 旋转设备屏幕                         | MOD+r                    |
| 展开通知面板                         | MOD+n \| 第 5 次点击     |
| 展开设置面板                         | MOD+n+n \| 双击 5 次点击 |
| 折叠面板                             | MOD+Shift+n              |
| 复制到剪贴板                         | MOD+c                    |
| 剪切到剪贴板                         | MOD+x                    |
| 同步剪贴板和粘贴                     | MOD+v                    |
| 注入电脑剪贴板文本                   | MOD+Shift+v              |
| 启用/禁用 FPS 计数器（在标准输出上） | MOD+i                    |
| 双指缩放                             | Ctrl+单击并移动          |




# 参考

[scrcpy投屏教程、scrcpy无线投屏、scrcpy命令大全-CSDN博客](https://blog.csdn.net/DDJ_TEST/article/details/120287342)

