# Kano LINE Blog Recovery

[简体中文](README.md) | [日本語](README.ja.md) | [English](README.en.md)

An offline recovery archive of Kano's LINE Blog, containing the original Japanese posts, Simplified Chinese versions, and the media referenced by both sets of posts.

## Contents

- `BLOG/`: Japanese originals, with 100 date-named posts.
- `BLOG_zh-cn/`: Simplified Chinese versions, with 100 date-named posts.
- `media/`: one shared media directory containing 314 files (265 JPG, 24 PNG, and 25 MP4 files).

Media links in both blog directories use `../media/...`, so both versions resolve to the same shared files.

## Posting Heatmap

Posts are grouped by publication month, with multiple retained versions counted once. The archive contains 99 unique articles; November 2015 had the most posts, with 7.

![Monthly posting heatmap](posting-activity-heatmap.svg)

## Content Type Statistics

The classification uses the Japanese originals in `BLOG/` and assigns each article one primary type based on its title and body. Articles covering multiple themes are counted under their main theme.

| Content type | Articles | Description |
| --- | ---: | --- |
| Daily life and interests | 38 | Daily notes, travel, food, hobbies, and essays |
| Performances and events | 22 | Concerts, tickets, events, conventions, and merchandise |
| Music and creative work | 21 | Singles, albums, music videos, recording, and creation |
| Fan interaction and Q&A | 10 | Greetings, questions, answers, and interaction |
| Anime, screen work, and collaborations | 8 | Anime, screen projects, and collaboration announcements |
| **Total** | **99** | Unique articles after deduplication |

## Split Video Archives

`5deac0f60979.mp4` and `ecc3e9bbd6b0.mp4` exceed GitHub's 100 MB per-file limit. To keep the article links such as `../media/...` unchanged, the repository stores gzip volumes in `media-parts/`; restored videos must be placed back at their original paths under `media/`.

On Windows, run these commands from the repository root:

```powershell
cmd /c copy /b "media-parts\5deac0f60979.mp4.tar.gz.part-*" "media-parts\5deac0f60979.mp4.tar.gz"
tar -xzf "media-parts\5deac0f60979.mp4.tar.gz" -C media
cmd /c copy /b "media-parts\ecc3e9bbd6b0.mp4.tar.gz.part-*" "media-parts\ecc3e9bbd6b0.mp4.tar.gz"
tar -xzf "media-parts\ecc3e9bbd6b0.mp4.tar.gz" -C media
```

On Unix systems, combine each set with `cat media-parts/<name>.part-* > <name>.tar.gz`, then run the same `tar -xzf ... -C media` command. The combined `.tar.gz` files are temporary and ignored by `.gitignore`.

## Reading

Open the posts in any Markdown-compatible reader.

## Source

Original blog path: <https://lineblog.me/kano/>

## Acknowledgements

Thanks to the [Internet Archive Wayback Machine](https://web.archive.org/) for preserving the historical pages and media used in this recovery archive.

Copyright for the posts, images, videos, and other media belongs to the original authors and respective rights holders. This project only organizes a local offline archive.
