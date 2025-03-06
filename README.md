# Benchmarking on Edge Devices

<details>
<summary><h2>Environment</h2></summary>

## General points
All benchmark are performed one-by-one with restarting kernel before running each cell.

## Raspberry Pi 5
1. Raspberry Pi OS Lite (64-bit).

2. Python 3.11.

3. Original source code and packages (poetry).

4. Active cooling.

## Orange Pi 5B
1. Ubuntu 22.04.

2. Python 3.11.

4. Original source code and packages (poetry).

4. Active cooling.

## Jetson Nano 4Gb
1. Ubuntu 20.04 Q-engineering.

2. Python 3.8.

3. Preinstalled Pytoch 1.13 with CUDA support.

4. One-time setup with the manually installed packages.

5. Slightly modified source code to fit Python 3.8 syntax and Pytorch 1.13, stored in a dedicated folder:
   
   - scaled_dot_product_attention is implemented in place;
   - minor syntax changes.

 </details>

## SuperPoint

descriptor_dim = 256, num_keypoints = 512, num_iterations = 10

### 256x256

|           Model                | Raspberry Pi 5 |
|--------------------------------|---------------:|
| SuperPoint                     |           4954 |
| SuperPointONNX                 |            296 |
| superpoint.onnx                |            147 |
| superpoint_I256_D256_K512.onnx |            153 |

### 1024x1024
|           Model                | Raspberry Pi 5 |
|--------------------------------|---------------:|
| SuperPoint                     |           5107 |
| SuperPointONNX                 |           4969 |
| superpoint.onnx                |           2860 |

## LightGlue

descriptor_dim = 256

num_keypoints = 512

num_iterations = 100

|           Model                | Image Size | Time (ms) |
|--------------------------------|------------|-----------|
| SuperPoint                     | 256x256    |      - |
|                                | 1024x1024  |      - |
| SuperPointONNX                 | 256x256    |        yy |
|                                | 1024x1024  |        xx |
| superpoint.onnx                | 256x256    |        yy |
|                                | 1024x1024  |        xx |
| superpoint_I256_D256_K512.onnx | 256x256    |        yy |
