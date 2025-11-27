# MMLab projects based on CUDA 12.6 and Pytorch 2.7.1.

This project contains mmengine, mmcv, mmdet, mmseg, mmpretrain, mmdet3d. All these six sub-projects has been built based on CUDA 12.6 and Pytorch 2.7.1.

|mmengine|mmcv|mmdet|mmseg|mmpretrain|mmdet3d|
|---|---|---|---|---|---|
|v0.8.5|v2.2.0|v3.3.0|v1.2.2|v1.2.0|v1.4.0|

# Install

## Prerequisites
Ensure CUDA toolkit is installed (CUDA 12.1+ compatible with CUDA 12.6 drivers):
```bash
# If CUDA toolkit not available, install locally:
wget https://developer.download.nvidia.com/compute/cuda/12.1.0/local_installers/cuda_12.1.0_530.30.02_linux.run
sh cuda_12.1.0_530.30.02_linux.run --silent --toolkit --toolkitpath=/path/to/cuda-12.1
export CUDA_HOME=/path/to/cuda-12.1
export PATH=$CUDA_HOME/bin:$PATH
export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH
```

## Installation Steps
```bash
# Install PyTorch with CUDA 12.1 support
pip install torch==2.5.1 torchvision==0.20.1 --index-url https://download.pytorch.org/whl/cu121

# Clone repository
git clone https://github.com/ezKernel/mmlab_cuda12.6_pytorch2.7.1.git
cd mmlab_cuda12.6_pytorch2.7.1

# Install mmengine (build from source)
cd mmengine_v0.8.5
python setup.py bdist_wheel
pip install dist/mmengine-0.8.5-py3-none-any.whl
cd ..

# Install mmcv (build with CUDA operations)
cd mmcv_v2.2.0
export MMCV_WITH_OPS=1
export MAX_JOBS=4
python setup.py bdist_wheel
pip install dist/mmcv-2.2.0-cp310-cp310-linux_x86_64.whl
cd ..

# Install mmdet (pre-built wheel)
pip install mmdet-3.3.0-cu126-mmdet-3.3.0-cu126_v0.2/dist/mmdet-3.3.0-py3-none-any.whl

# Install mmsegmentation (pre-built wheel)
pip install mmseg-1.2.2-cu126-mmseg-1.2.2-cu126_v0.2/dist/mmsegmentation-1.2.2-py3-none-any.whl

# Install mmpretrain (build from source)
cd mmpretrain_v1.2.0
python setup.py bdist_wheel
pip install dist/mmpretrain-1.2.0-py3-none-any.whl
cd ..

# Install mmdet3d (build from source with version compatibility fix)
cd mmdet3d_v1.4.0
python setup.py bdist_wheel
pip install dist/mmdet3d-1.4.0-py3-none-any.whl
cd ..
```

**Note**: mmdet3d_v1.4.0 has been patched to support mmcv 2.2.0 (original only supports <2.2.0)



----
🎉🎉🎉🎉 Acknowledgement: Thanks to Morgan LT (https://github.com/KaceCM).
