# Kano LINE Blog Recovery

[简体中文](README.md) | [日本語](README.ja.md) | [English](README.en.md)

鹿乃（Kano）LINE Blog 的离线恢复档案，包含日文原文、简体中文版本及文章媒体文件。

## 内容

- `BLOG/`：日文原文，100 篇按日期命名的文章。
- `BLOG_zh-cn/`：简体中文版本，100 篇按日期命名的文章。
- `media/`：两个版本共享的媒体目录，共 314 个文件（265 JPG、24 PNG、25 MP4）。
- `archive/`：辅助元数据、恢复报告、统计文件和原始 ZIP 备份；该目录已加入 `.gitignore`，只保留本地归档。
- `archive/article-id-map.json`：LINE Blog 文章 URL 与文章 ID 的映射。
- `archive/media-name-map.json`：恢复前媒体名称与本地文件名的映射。
- `archive/version-diff-report.md` / `archive/version-diff-report.json`：保留版本之间的差异报告。
- `archive/posting-activity-by-month.csv` / `posting-activity-heatmap.svg`：发文活动统计。

文章中的媒体链接统一使用 `../media/...`，因此两个博客目录都可以使用同一份媒体文件。

## 发帖统计

按文章发布日期统计，多个版本只计一次，共 99 篇去重文章；2015 年 11 月发帖最多，共 7 篇。

![按月份统计的发帖热力图](posting-activity-heatmap.svg)

## 内容类型统计

以下分类以 `BLOG/` 的日文原文为基准，按标题和正文判断主内容。混合主题文章只计入一个主要类别。

| 内容类型 | 文章数 | 说明 |
| --- | ---: | --- |
| 日常生活与兴趣 | 38 | 日常记录、旅行、饮食、兴趣和随笔 |
| 演出与活动 | 22 | 演唱会、票务、活动、展会和周边 |
| 音乐创作与作品 | 21 | 单曲、专辑、MV、录音和创作 |
| 粉丝互动与问答 | 10 | 问候、提问、回答和互动 |
| 动画、影视与合作 | 8 | 动画、影视作品及合作宣传 |
| **合计** | **99** | 去重后的文章数 |

## 大文件视频分卷

`5deac0f60979.mp4` 和 `ecc3e9bbd6b0.mp4` 均超过 GitHub 的 100 MB 单文件限制。为保持文章中的 `../media/...` 引用不变，仓库保存的是 `media-parts/` 中的 gzip 分卷；还原后的视频必须放回 `media/` 原路径。

Windows 下，在仓库根目录运行：

```powershell
cmd /c copy /b "media-parts\5deac0f60979.mp4.tar.gz.part-*" "media-parts\5deac0f60979.mp4.tar.gz"
tar -xzf "media-parts\5deac0f60979.mp4.tar.gz" -C media
cmd /c copy /b "media-parts\ecc3e9bbd6b0.mp4.tar.gz.part-*" "media-parts\ecc3e9bbd6b0.mp4.tar.gz"
tar -xzf "media-parts\ecc3e9bbd6b0.mp4.tar.gz" -C media
```

Unix 系统可用 `cat media-parts/<name>.part-* > <name>.tar.gz` 合并分卷，再运行同样的 `tar -xzf ... -C media`。合并后的 `.tar.gz` 只是临时文件，已被 `.gitignore` 忽略。

## 阅读

直接在支持 Markdown 的阅读器中打开文章即可。

## 致谢

感谢 [Internet Archive Wayback Machine](https://web.archive.org/) 提供历史页面和媒体恢复所需的网页存档。

文章、图片、视频及其他媒体的版权归原作者和相应权利人所有。本项目仅整理本地离线档案。

原始博客路径：<https://lineblog.me/kano/>
