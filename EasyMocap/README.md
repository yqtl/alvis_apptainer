#How to use
```bash
apptainer build easymocap.img easymocap.def
apptainer shell --fakeroot --writable-tmpfs easymocap.img
```
#Notes on the container
- The container is based on nvcr.io/nvidia/cuda:11.7.1-devel-ubuntu20.04, no CuDNN is included, but CUDA must >= 11 to be compatible with Nvidia 30xx cards.
- Mesa is installed to support OpenGL rendering. OpenPose is built under /workspace/OpenPose/build. EasyMocap is built under /workspace/EasyMocap.
- PyTorch3D is installed using pip from git repo. Ninja is not installed/used during wheel building.
- Soft link is created for SMPL model and comment easymocap/assignment/criterion.py:line 69 with return 1 to avoid missing detection of person.