# 沙尘暴环境声设计

基础实践 2 期末作业，以《死亡搁浅 2》的沙尘暴场景为参考，使用 Audition 处理声音素材，并在 Wwise 中搭建可持续播放的环境声。

设计以循环风沙底声为基础，叠加随机出现的沙粒滑动、金属抖动、杂物落地与雷声，通过播放间隔、音量、音高和空间位置的变化丰富环境氛围。完整的场景分析、素材处理过程和工程参数见 [设计报告](Report/Report.md)。

## 目录

```text
Repo/
├─ Assets/                         # 19 个处理后的 WAV 音频
├─ Report/
│  ├─ Report.md                    # 设计报告
│  └─ images/                      # 场景参考截图
├─ WwiseProject/
│  └─ SHU_GADEx_FinalProject/
│     ├─ SHU_GADEx_FinalProject.wproj
│     ├─ Originals/                # 工程引用的音源及插件素材
│     └─ …                         # 容器、事件、衰减等工作单元
├─ .gitignore
└─ README.md
```

## 打开与试听

工程文件记录的版本为 **Wwise 2025.1.8，Build 9170**，目标平台为 Windows。

1. 使用该版本 Wwise 打开 [SHU_GADEx_FinalProject.wproj](WwiseProject/SHU_GADEx_FinalProject/SHU_GADEx_FinalProject.wproj)。
2. 在 Events 中选择 `Play_AMB_Desert_SandStorm`，通过 Transport Control 播放，试听完整环境声。
3. 雷电事件首次延迟为 15～25 秒，之后每轮事件结束后间隔 25～45 秒；可持续试听数分钟，观察各声音层的随机变化。
4. 播放 `Stop_AMB_Desert_SandStorm` 可用 1 秒淡出停止环境声。

工程已包含 `Originals/SFX/` 音源，可直接在 Wwise 中试听。`Assets/` 保存处理后的素材副本；编辑外部副本后，需要同步到工程引用的音源才能影响播放。

## 声音组成

| 声音层 | 文件数 | 播放方式 |
| --- | ---: | --- |
| 风沙底声 Bed | 1 | 持续循环 |
| 沙粒滑动 | 4 | 随机选材、随机间隔 |
| 金属抖动 | 4 | 随机选材、随机间隔 |
| 杂物落地 | 4 | 随机选材、随机间隔 |
| 炸雷 Clap | 3 | 每次雷电事件有 40% 概率加入 |
| 滚雷 Rumble | 3 | 每次雷电事件必播 |

共 19 个 WAV，格式为 48 kHz、24 bit、双声道 PCM。沙粒、金属、杂物和炸雷使用空间定位及距离衰减，Bed 与滚雷维持宽阔的立体声环境感。

## 素材来源

声音素材来自 Freesound、ZapSplat 及在线视频，具体作者、原始素材链接和处理方式见 [报告中的素材说明](Report/Report.md#声音素材获取与处理)。场景截图用于说明设计参考，图中保留了原视频水印。

第三方音频及截图的权利归原权利人所有，使用和再分发应遵守各素材原有许可；本项目未对这些素材另行授予许可。