# 无人车与无人艇目标检测数据集（UGV–USV Detection Dataset）

完整数据集包含 **725 张图片、725 份 YOLO 标签和 818 个矩形标注框**。类别编号为 `0` 无人车（UGV）和 `1` 无人艇（USV）。仓库提供 20 对样例，完整压缩包由 Zenodo 托管。

## 数据划分

| 压缩包目录 | 图片 | 标签文件 | 无人车框 | 无人艇框 | 总框数 |
|---|---:|---:|---:|---:|---:|
| `train/` | 632 | 632 | 371 | 336 | 707 |
| `valid/` | 93 | 93 | 57 | 54 | 111 |
| **合计** | **725** | **725** | **428** | **390** | **818** |

两个划分中的每张图片都配有至少一个标注框。压缩包没有单独的测试集。根据包内的 Roboflow 导出说明，本次导出未应用图像增广。

### 复现配套实验时使用的 622 张训练图

压缩包的训练集有 **632 张**。配套 YOLO26 实验保留全部 **93 张验证图**，从训练清单中排除了与验证图重复的 **10 张训练图**，其中包括缩放副本。复现实验时使用剩余的 **622 张训练图**。清单列出了每对图片的路径和 SHA-256，便于核对。[实验排除的 10 对重复图](https://github.com/Britney-codemax/yolo26-vit-driverless-vehicle/blob/main/training/configs/verified_v4_duplicates.csv)

## 下载与校验

在 [Zenodo 下载页](https://doi.org/10.5281/zenodo.23794441) 的文件列表中选择 `dataset.zip`。该记录下的文件已更新，复现实验时请同时核对压缩包的 SHA-256。

| 项目 | 内容 |
|---|---|
| 文件名 | `dataset.zip` |
| 文件大小 | 175,960,324 字节 |
| 当前记录 DOI | [10.5281/zenodo.23794441](https://doi.org/10.5281/zenodo.23794441) |
| 全版本 DOI | [10.5281/zenodo.23794440](https://doi.org/10.5281/zenodo.23794440) |
| Zenodo 记录版本 | `v1.0.0` |
| 包内 Roboflow 导出版本 | `v4 No Negative 11.20` |
| MD5 | `a92b5e9ab636d9c34ebbc66381c01879` |
| SHA-256 | `3303bd0666f4e9521c27df4226a32a6ab868461af3c3876abbb7a6efe7b301e5` |

## 文件与标注

解压后，`dataset/data.yaml` 定义类别顺序和训练、验证路径。

```text
dataset/
├── data.yaml
├── train/
│   ├── images/
│   └── labels/
└── valid/
    ├── images/
    └── labels/
```

图片与同一划分下的标签按文件主名配对。每行标注一个目标，字段依次为 `class_id x_center y_center width height`。横向坐标和框宽按图像宽度归一化，纵向坐标和框高按图像高度归一化，取值范围为 0 到 1。

GitHub 上的 20 对样例均取自压缩包的训练集，无人车、无人艇各 10 对。仓库保留短编号，例如 [15.jpg](sample/imgs/15.jpg) 与 [15.txt](sample/labels/15.txt) 对应压缩包中以 `15_jpg.rf.` 开头的图片与标签。[浏览样例图片](sample/imgs/) · [浏览对应标签](sample/labels/)

## 数据来源与使用说明

图片来自已有公开数据集、网络收集的照片，以及项目组对上海交通大学购置的无人车和无人艇的实拍。包内导出说明列出了 [Roboflow 项目来源](https://universe.roboflow.com/yans-workspace-47kt2/driverless-vehicle-iv6qt)。

第三方图片的权利归原权利人，部分图片的再分发授权仍待核实。使用前请阅读 Zenodo 记录的使用说明，按要求注明来源并引用 DOI。反馈标注或权属问题时，请附上样例编号或压缩包内的文件路径。[提交反馈](https://github.com/Britney-codemax/ugv-usv-dataset/issues)
