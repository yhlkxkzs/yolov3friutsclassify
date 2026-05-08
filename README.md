# yolov3friutsclassify

GitHub 侧用于存放**水果检测**推理权重（训练自 **`yolov3-tiny.pt`**，与 log 中 **v3** 一路一致），供 Actions 或本地脚本使用。

**说明**：该 `best.pt` 为 **Ultralytics YOLOv5 仓库**保存的检测 checkpoint（与新版 `ultralytics.YOLO` **不兼容**）。推理使用 **`torch.hub.load('ultralytics/yolov5', 'custom', path=...)`**，见 `scripts/infer_fruit_detect.py`。

**移动端对接**：见 **[docs/MOBILE_APP_INTEGRATION.md](docs/MOBILE_APP_INTEGRATION.md)**。  
可选 Secrets：`FRUIT_SERVER_UPLOAD_URL`、`FRUIT_SERVER_UPLOAD_TOKEN`（与 MobileNet / YOLOv8 仓库行为一致）。

## 当前权重

| 文件 | 说明 |
|------|------|
| `models/yolov3_tiny_fruit_detect_best.pt` | **YOLOv3-tiny** 检测 `best.pt` |

- **类别数**：6（与 checkpoint 内 `names` 一致）  
- **类别名**：见 `models/classes.json`  
- **来源 run**：`fruit_detection_formal100_20260430_164036`  
  本地原路径：  
  `YOLO/versions/v3/runs/train/fruit_detection_formal100_20260430_164036/weights/best.pt`

## 本地推理

```bash
pip install torch torchvision  # 或 CPU: --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt
python scripts/infer_fruit_detect.py --device cpu incoming/your.jpg
```

首次运行会从 PyTorch Hub 拉取 **`ultralytics/yolov5`**（需联网）。

## GitHub Actions

向 **`incoming/`** 推送图片即触发 **Fruit detection (YOLOv3-tiny / YOLOv5 hub)**，或在 Actions 里 **Run workflow**。结果见 Summary 与 Artifacts 中的 `predictions.json`。

## 克隆

```bash
git clone git@github.com:yhlkxkzs/yolov3friutsclassify.git
```
