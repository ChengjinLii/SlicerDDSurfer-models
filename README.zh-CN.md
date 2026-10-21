<div align="center">

# SlicerDDSurfer 运行资源

[代码](https://github.com/ChengjinLii/SlicerDDSurfer) | [资源分组](#资源分组) | [授权说明](RESOURCE_NOTICES.md) | [English](README.md)

</div>

---

仓库保留 `SlicerDDSurfer-models` 名称以兼容既有地址，但不只保存权重：
模型、图谱、模板及必要的大型非代码运行资源均在此分组管理。
默认 core 仍只有原有 31 个解剖资源；其他资源按需获取，不随插件代码全量下载。

---

## 资源分组

| 路径 | 内容 |
| --- | --- |
| `surface/`、`segmentation/`、`parcellation/` | 原有 DDSurfer、DDSeg、DDParcel 权重及模板 |
| `brain_mask/pnl_cnn/` | 三方向权重、网络结构、完整原许可；IIT 模板仅本地保留且 Git 忽略 |
| `brain_mask/synthstrip/` | 作者提供的版本 1 主模型，采用 CC BY 4.0 许可选项 |
| `bundles/tractcloud/` | 最小推理权重、参数、308 字节图谱参考、原许可 |
| `bundles/wma/archives/` | 两个固定版本的 ORG 官方 ZIP；不重复提交解压目录 |

PNL 与 TractCloud 的权重不能笼统改标为本项目 BSD 许可；须保留各自完整协议与引用。
WMA/ORG 官方 Zenodo 记录采用 CC BY 4.0；同时保留上游附带的 Slicer 协议。
**IIT 模板未经书面许可不得上传网站或其他电子媒介**，因此它不是本仓库的镜像内容。
本地拥有或成功校验文件，并不等于取得再分发许可。

---

## 清单与获取

`asset_mirror_manifest.json` 继续描述原有 core，避免覆盖已有发布记录。
可选资源单独记录为 `optional_assets_mirror_manifest.json` 与
`optional_assets_mirror_index.tsv`。代码仓库中的
`models/external_assets_manifest.json` 保存可信摘要、大小、来源及分发策略。

当前整理了本地资源，不代表新增大文件已经推送 GitHub。
镜像地址在远端文件完成验证前保持 planned；不要把待上传目录宣传为已可下载。

从代码仓库验证本地目录：

```bash
python3 scripts/download_model_assets.py \
  --manifest models/external_assets_manifest.json \
  --profile mirrorable-inference \
  --asset-root /path/to/SlicerDDSurfer-models --verify-only
```

完整 PNL 本地检查使用 `--profile pnl-cnn`；该组合包括受限 IIT 模板，
导出工具会拒绝把整个组合打入镜像。WMA 解压内容可从受校验 ZIP 重新生成，
本地索引记录每个解压文件的 SHA256。

---

## 不纳入的文件

Python/Conda 环境、CUDA 库、FSL/MRtrix/FreeSurfer 程序、安装器缓存仍由独立 runtime 管理。
不迁入用户 DWI、临床数据、训练/测试数据集、分析输出及逐被试生成的拟合字典。
资源齐全也不代表对应软件、GPU 或科学 QC 已通过。
