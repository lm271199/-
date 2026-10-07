# 计算机视觉实验报告

计算机视觉课程实验代码与实验报告仓库，本仓库包含课程各次实验的实验报告与相关代码。

## 实验列表

- [实验一：计算机视觉库的安装](./实验一_计算机视觉库的安装.md)

---

## 实验一：计算机视觉库的安装

### 一、实验目的

1. 掌握 Anaconda 的安装与基本操作；
2. 掌握 conda 虚拟环境的创建与管理；
3. 完成 OpenCV 的安装与配置；
4. 完成 PyTorch 的安装与环境验证（本次使用 CPU 版本）。

### 二、实验环境

| 项目 | 版本 / 信息 |
| --- | --- |
| 操作系统 | Windows |
| Anaconda | 2025.06-0（conda 25.5.1） |
| 虚拟环境 | cv（Python 3.11.16） |
| OpenCV | opencv-python 5.0.0.93 |
| PyTorch | torch 2.14.0+cpu / torchvision 0.29.0 |
| 显卡 | NVIDIA GeForce RTX 4060（驱动 566.07） |

### 三、实验内容

#### 1. Anaconda 的安装及配置

Anaconda 安装过程较为简单：从官网下载安装包，按向导完成安装即可。安装完成后自带 conda 包管理器，用于虚拟环境与依赖包的管理。

#### 2. conda 的基本操作与 OpenCV 的安装

创建名为 `cv` 的虚拟环境并指定 Python 版本：

```bash
conda create -n cv python=3.11
```

进入虚拟环境：

```bash
conda activate cv
```

安装 OpenCV：

```bash
pip install opencv-python
```

验证安装结果：

```bash
python -c "import cv2; print(cv2.__version__)"
```

运行输出：

```
5.0.0.93
```

#### 3. GPU 加速环境配置

本实验原计划安装 NVIDIA CUDA Toolkit 与 cuDNN 以获得 GPU 加速能力。考虑到实际学习需求，本次实验改用 **CPU 版本 PyTorch** 完成环境搭建，无需安装 CUDA Toolkit 与 cuDNN，后续学习基础 CV 算法时完全够用；如后续需要训练深层网络，再补充安装 GPU 版环境即可。

#### 4. PyTorch 安装

在 `cv` 环境中安装 CPU 版 PyTorch 与 torchvision：

```bash
pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
```

查看已安装的 PyTorch：

```bash
conda list pytorch
```

输出（节选）：

```
torch          2.14.0+cpu
torchvision    0.29.0
```

#### 5. PyTorch 环境验证

在 `cv` 环境中运行验证代码：

```bash
python -c "import torch; print(torch.__version__)"
```

输出：

```
2.14.0+cpu
```

由于使用 CPU 版本，GPU 相关接口返回预期结果：

```python
import torch

print(torch.cuda.is_available())          # False（CPU 版预期结果）
print(torch.backends.cudnn.is_available())# False（CPU 版预期结果）
```

CPU 版张量运算验证（正常可用）：

```python
import torch

x = torch.rand(3, 3)
print(x)
```

### 四、实验总结

1. 本次实验较为基础，主要是为后续计算机视觉实验搭建实验环境；
2. 熟悉了 Anaconda 虚拟环境管理的基本操作（创建、激活、安装依赖包）；
3. 完成了 OpenCV 的安装与配置，并安装了 CPU 版 PyTorch；
4. 由于选择 CPU 版 PyTorch，本次未配置 CUDA 与 cuDNN，GPU 相关接口返回 False 属预期结果，不影响基础 CV 实验的开展。
