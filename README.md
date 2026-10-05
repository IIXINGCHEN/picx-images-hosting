# picx-images-hosting

图澜 Image API Platform 的图片存储仓库。所有图片统一为 **WebP** 格式，文件名即内容 SHA-256（天然去重），通过 jsDelivr CDN 对外提供访问。

## 目录结构

按**内容**组织（英文小写扁平命名），来源信息由平台数据库维护：

| 目录 | 说明 |
|---|---|
| `anime/` | 动漫（含二次元、游戏、虚拟主播、角色） |
| `scenery/` | 风景、星空 |
| `portrait/` | 人像 |
| `pets/` | 萌宠 |
| `misc/` | 待分类 / 其他 |

## 访问方式

通过 jsDelivr（`@master` 分支）：

```
https://cdn.jsdelivr.net/gh/IIXINGCHEN/picx-images-hosting@master/<目录>/<sha256>.webp
```

示例：

```
https://cdn.jsdelivr.net/gh/IIXINGCHEN/picx-images-hosting@master/anime/xxx.webp
```

## 图片规范

- 格式：WebP（quality 85）
- 命名：`{sha256}.webp`，相同内容只存一份
- 元数据（尺寸、分类、标签、来源）由图澜平台 D1 数据库维护，本仓库只存图片文件

## 自动采集

图片由图澜采集管线自动拉取、去重、转码后提交到本仓库（commit 信息以 `ingest:` 开头）。请勿手动上传重名文件；如需删除图片，请同步通知平台方删除 D1 中的索引记录。
