# aisee-comic-to-drama

把漫画/图片剧情改编为真人短剧视频的 Agent Skill。

## 工作流概览

1. **素材理解与人物真人化** — 按漫画剧情重写提示词与图片资产，人物转真人；生成 4 张主角形象图供用户选择，多主角则多步逐一确认。
2. **分镜参考图** — 漫画每个画面都生成出来作为分镜参考图。
3. **剧本与时间拆解** — 拆解总时间 / 小段时间 / 分镜时间；每小段 10-15s，分镜时间不平均；剧本先给用户确认。
4. **剪辑规则** — 按分镜顺序平铺，镜与镜直切，不叠化、不闪回、不倒放。
5. **生成平台路由** — bitahub 工作流链接 → bitahub；json api → 本地 ComfyUI；runninghub 工作流链接 → runninghub（需 api key）；未提供 → 询问用哪个平台的 seedance。
6. **收尾** — 分段结果合并为一个视频放桌面；bitahub 实例使用后在 https://www.bitahub.studio/instances 关机。

## 安装

使用 [skills CLI](https://github.com/vercel-labs/skills) 安装：

```bash
# 列出本仓库中的 skill
npx skills add <你的用户名>/aisee-comic-to-drama --list

# 安装
npx skills add <你的用户名>/aisee-comic-to-drama --skill aisee-comic-to-drama
```

或直接克隆：

```bash
git clone https://github.com/<你的用户名>/aisee-comic-to-drama.git
```

## 文件说明

- `SKILL.md` — skill 主文件，含 frontmatter（name / description）与完整工作流。
- `LICENSE` — MIT。

## 参考

提示词书写规则：[MiniMax H3 skills](https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills)
