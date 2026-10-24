# aisee-comic-to-drama

把漫画/图片剧情改编为真人短剧视频的 Agent Skill。

## 工作流概览

1. **素材理解与人物真人化** — 按漫画剧情重写提示词与图片资产，人物转真人；生成 4 张角色形象图供用户选择，多角色则多步逐一确认。
2. **角色语音预生成** — 按角色侧画提前生成对应语音，供工作流参考，统一角色音色。
3. **分镜参考图** — 漫画每个画面都生成出来作为分镜参考图。
4. **剧本与时间拆解** — 拆解总时间 / 小段时间 / 分镜时间；每小段 10-15s，分镜时间不平均；剧本先给用户确认。
5. **剪辑规则** — 按分镜顺序平铺，镜与镜直切，不叠化、不闪回、不倒放。
6. **生成平台路由** — bitahub 工作流链接 → bitahub；json api → 本地 ComfyUI；runninghub 工作流链接 → runninghub（需 api key）；未提供 → 询问用哪个平台的 seedance（不使用 minimax 提示词书写 skill）。
7. **bitahub 节点参考** — 参考图节点 153/155/152/154/156/178，参考音频节点 182/183/184，时长节点 17，提示词节点 116；节点 20/146 为一采/二采，宽高比一致、二采分辨率为一采 1.5 倍；实例用完后在 https://www.bitahub.studio/instances 关机。
8. **收尾** — 分段结果合并为一个视频放桌面。

## 安装

使用 [skills CLI](https://github.com/vercel-labs/skills) 安装：

```bash
# 列出本仓库中的 skill
npx skills add annalyseg805-blip/aisee-comic-to-drama --list

# 安装
npx skills add annalyseg805-blip/aisee-comic-to-drama --skill aisee-comic-to-drama
```

或直接克隆：

```bash
git clone https://github.com/annalyseg805-blip/aisee-comic-to-drama.git
```

## 文件说明

- `SKILL.md` — skill 主文件，含 frontmatter（name / description）与完整工作流。
- `LICENSE` — MIT。

## 参考

提示词书写规则：[MiniMax H3 skills](https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills)
