## Notes

1. **Environment Requirements**: The script pulls the NGC CUDA 11.1.1 image, without cuDNN. I opted to compile PyTorch from scratch due to runtime core dumps when using the pre-compiled PyTorch in `nvcr.io/nvidia/pytorch:20.12-py3` on KTH-cloud. The usage of Conda within `nvcr.io/nvidia/pytorch:20.12-py3` for MMHuman3D installation hasn't been tested.

2. **PyTorch and Torchvision Installation**: The base image does not come with PyTorch or Torchvision pre-installed. The installation of these packages is handled by the script itself. The script chooses the PyTorch and Torchvision versions that are compatible with the installed CUDA version.

3. **PyTorch3D Installation**: The script installs PyTorch3D from source. Ensure that your environment supports CUDA for this to work properly. Be aware that PyTorch3D versions are specific to certain PyTorch versions and might not be backward compatible. Choose the right PyTorch3D version based on the PyTorch version installed.

4. **Data Models**: This script fetches several data models from external sources. Please be aware that these download links can expire or change over time, which may cause the downloads to fail.

5. **Directory Creation**: The script uses the `cd` command in combination with relative paths to create necessary directories.

## Usage

Hybrik not supoprted by mmhuman3d
```bash
python3 demo/pymafx_estimate_smplx.py --input_path <input_path> --output_path <output_path> --visualization
```

```bash
python3 demo/estimate_smplx.py \
--mesh_reg_config configs/expose/expose.py \ 
--mesh_reg_checkpoint  data/pretrained_models/expose.pth \
--single_person_demo \
--det_config demo/mmdetection_cfg/faster_rcnn_r50_fpn_coco.py \
--det_checkpoint https://download.openmmlab.com/mmdetection/v2.0/faster_rcnn/faster_rcnn_r50_fpn_1x_coco/faster_rcnn_r50_fpn_1x_coco_20200130-047c8118.pth \
--input_path  <input_path>  --show_path <output_path> --output <output_path> --draw_bbox
```
