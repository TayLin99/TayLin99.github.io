# 素材图片规范

## 格式要求

- **格式**: WebP（支持透明通道）
- **尺寸**: **2048 × 2048** 像素
- **色彩**: RGBA（32-bit，带 Alpha 透明）

## 说明

所有部件素材统一使用 **2048×2048 的画布**，部件内容放在画布中对应的位置，其余区域保持透明。

不同部件的图片直接叠加即可正确对位，无需额外的坐标/裁剪参数。

## PNG → WebP 转换

推荐使用 Pillow（Python）一行命令批量转换，保留透明通道、质量 88%：

```bash
pip install Pillow
python -c "
from PIL import Image
import os
for f in os.listdir('.'):
    if f.endswith('.png'):
        img = Image.open(f)
        img.save(f.replace('.png','.webp'), 'WEBP', quality=88, method=6)
        print(f'{f} -> webp')
"
```

也可用 ImageMagick：

```bash
magick mogrify -format webp -quality 88 *.png
```

## 目录结构

```
res/
├── 背景/       # 背景图
├── 身体/       # 身体底图
├── 狗毛/       # 头发
├── 眉毛/
├── 眼睛/
├── 鼻子/
├── 鼻子装饰/
├── 腮红/
├── 嘴/
├── 衣服/
├── 手部配饰/
├── 配饰1/
├── 配饰2/
├── 配饰3/
└── 部位14/
```

每个部位文件夹内可以放多张 WebP 作为不同选项，文件名无特殊要求。
