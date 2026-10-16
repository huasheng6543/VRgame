# VR Game（太空 VR 交互游戏）

一个基于 Unity + XR Interaction Toolkit 开发的太空主题 VR 游戏 Demo。玩家置身于一艘太空船中，可以驾驶飞船穿越银河、使用激光手枪击碎太空垃圾与陨石，并通过真实的双手交互操作舱内设备。

## 环境要求

| 项目 | 版本 |
| --- | --- |
| Unity | 2022.3.62f2c1 (LTS) |
| 渲染管线 | Universal Render Pipeline (URP) 14.0.12 |
| XR Interaction Toolkit | 2.6.5 |
| OpenXR | 1.14.3 |
| XR Plug-in Management | 4.5.3 |

支持 OpenXR 兼容的 VR 头显（Meta Quest 系列、Valve Index、HTC Vive 等）。

## 快速开始

1. 使用 Unity Hub 安装 **Unity 2022.3.62f2c1**（或相近的 2022.3 LTS 版本）。
2. 克隆本仓库后，用 Unity Hub 将项目文件夹添加为现有项目并打开。
3. Unity 会自动根据 `Packages/manifest.json` 还原依赖包。
4. 打开主场景 `Assets/Scenes/SampleScene.unity`。
5. 在 **Project Settings > XR Plug-in Management** 中确认已启用 OpenXR，并配置好你的头显运行时。
6. 连接头显后点击 Play，或构建到目标平台运行。

## 玩法与核心功能

- **飞船驾驶**：通过舱内的推杆（XRLever）控制前进，旋钮（XRKnob）控制转向。
- **激光手枪**：抓取科幻手枪并扣动扳机，发射激光束持续击碎命中的可破坏物体。
- **可破坏物体**：太空垃圾/陨石被激光照射一段时间后碎裂成碎片。
- **垃圾回收**：将太空垃圾投入回收舱，触发区域自动清理。
- **物理按钮开门**：按下 3D 按钮切换舱门开启动画。
- **标签过滤插槽**：Socket 交互点仅接收指定 Tag 的物体。
- **手部动画**：Oculus 手部模型与终结者机械手，根据手柄输入播放握持/捏合动画，抓取物体时自动隐藏手部模型。

## 自定义脚本一览（Assets 根目录）

| 脚本 | 功能 |
| --- | --- |
| `SpaceOutsideController.cs` | 读取推杆/旋钮数值，驱动飞船移动与转向 |
| `MeteorPistol.cs` | 抓取激活后发射激光射线，命中物体时触发其 `Break` |
| `Breakable.cs` | 持续受击计时，到时后分裂为碎片 |
| `TrashCan.cs` / `TriggerZone.cs` | 触发区域事件，回收进入的太空垃圾 |
| `ButtonPushOpenDoor.cs` | 按钮交互切换门动画布尔值 |
| `XRSocketTagInteractor.cs` | 按 Tag 限制 Socket 可交互物体 |
| `DisableGrabbingHandModel.cs` | 抓取时隐藏手部模型 |

## 项目结构

```
Assets/
├── Lets Make a VR Game/   # 核心游戏资源（手部、手枪、垃圾、3D UI 示例等）
├── Samples/               # XR Interaction Toolkit 官方 Starter Assets
├── Scenes/                # 游戏场景（SampleScene 为主场景）
├── Sci-Fi Styled Modular Pack/  # 科幻模块化环境资源包
├── Settings/              # URP 渲染管线配置
├── XR/                    # OpenXR 配置
└── XRI/                   # XR Interaction Toolkit 配置
```

## 素材来源

- XR Interaction Toolkit Starter Assets（Unity 官方示例）
- "Lets Make a VR Game" 教程配套资源
- Sci-Fi Styled Modular Pack
- Oculus Hands / Terminator Hand 模型

## 许可证

本项目仅用于学习交流。第三方素材的版权归其原作者所有，请遵循各素材原始许可条款。
