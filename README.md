# picx-images-hosting

图澜 Image API Platform 的图片存储仓库。所有图片统一为 **WebP** 格式，文件名即内容 SHA-256（天然去重），通过 jsDelivr CDN 对外提供访问。

## 目录结构

| 目录 | 说明 | 来源 |
|---|---|---|
| `dongman/` | 动漫图片（初始 270 张） | 原始图库 |
| `images/` | 通用图片（初始 385 张） | 原始图库 |
| `acg/` | ACG 随机图（持续增长） | app.zichen.zone 采集 |
| `moehu/` | MoeHu 图集（按图集分子目录，持续增长） | img.moehu.org 采集 |
| `fuchen/` | 浮尘随机图（`dongman/` 动漫、`fengjing/` 风景） | api.fuchenboke.cn 采集 |

`moehu/` 子目录即图集 ID（如 `img1`、`sjpic`、`ys`、`cat`），每个子目录最多保留 50 张精选。

## 访问方式

通过 jsDelivr（`@master` 分支）：

```
https://cdn.jsdelivr.net/gh/IIXINGCHEN/picx-images-hosting@master/<目录>/<sha256>.webp
```

示例：

```
https://cdn.jsdelivr.net/gh/IIXINGCHEN/picx-images-hosting@master/moehu/ys/xxx.webp
```

## 图片规范

- 格式：WebP（quality 85）
- 命名：`{sha256}.webp`，相同内容只存一份
- 元数据（尺寸、分类、标签、来源）由图澜平台 D1 数据库维护，本仓库只存图片文件

## 自动采集

图片由图澜采集管线自动拉取、去重、转码后提交到本仓库（commit 信息以 `ingest:` 开头）。请勿手动上传重名文件；如需删除图片，请同步通知平台方删除 D1 中的索引记录。
