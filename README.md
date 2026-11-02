# shuai-illustration-gen

![shuai-illustration-gen：把想法画成插画，黑色铅笔的纸带笔触化为朱红翅膀的飞鸟，展示米白纸底与剪纸拼贴风格。](assets/readme/hero.png)

生成风格统一的复古编辑概念插画：暖米白纸底、黑白灰主体、朱红强调、手工剪纸拼贴与细腻印刷颗粒。

适合文章配图、抽象概念表达和系列插画。风格规范全部写在 [SKILL.md](SKILL.md) 中，无需附带或读取固定参考图片。

## 文章配图案例

| 一纸合同与交付成本 | 主业与副业，同根而生 |
| --- | --- |
| ![天平左侧是一页合同，右侧的文件和工具压低了秤盘](assets/readme/examples/contract-and-work.png) | ![两枝结出不同数量果实的树，共用同一片根系](assets/readme/examples/shared-roots.png) |

| 被工作挤压的成长空间 | 开锁的三秒值多少钱？ |
| --- | --- |
| ![背着文件夹的人弯下腰，伸手去够一株幼苗](assets/readme/examples/work-and-growth.png) | ![锁匠站在巨大的锁孔旁，红色台阶穿过锁孔通向门后](assets/readme/examples/value-of-unlocking.png) |

## 安装

将仓库克隆到支持 Agent Skills 的工具所读取的技能目录，例如：

```bash
git clone https://github.com/qizong007/shuai-illustration-gen.git ~/.agents/skills/shuai-illustration-gen
```

目标目录已存在时，先检查现有安装，避免覆盖。使用其他技能目录的工具，可调整克隆位置。

## 使用

```text
用 $shuai-illustration-gen 画一张表达「注意力被分散」的插画。
```

也可以提供文章或段落，指定画幅、数量或仅输出提示词。默认生成一张横向 3:2 无字插画；实际出图需要环境提供图像生成工具，Codex 中优先使用内置 image_gen。

## 视觉规范

| 用途 | 目标色 |
| --- | --- |
| 米白背景 | `#FBF8F1` |
| 主黑色 | `#171717` |
| 纸张白 | `#F7F5EF` |
| 辅助灰 | `#BDB9B0` |
| 强调红 | `#D32918` |

默认围绕一个视觉隐喻构图，保留能说明主体关系的物件，让其余区域留白。朱红约占整幅画面的 10%–20%，集中在最值得注意的形体上。
