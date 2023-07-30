Build from preprocess_blending.def first, which installs jupyter and mmpose.


Start jupyter container, under Alvis env:
```console
    container=xxx.sif
    apptainer exec --nv $container jupyter notebook --config="${CONFIG_FILE}"
```
Go to forked version of smplify-x-partial ipynb notebook.
Do MMpose prediction, then blend with openpose(seperate predict).


Then build smplify-x-partial.def for smplx prediction.

Post building
```console
# Download smplx_parts_segm.pkl and smplx model
cd /workspace
wget https://owncloud.tuebingen.mpg.de/index.php/s/MWnr8Kso4K8T8at/download/smplx_parts_segm.pkl
wget -O models_smplx_v1_1.zip https://kth-my.sharepoint.com/:u:/g/personal/qyuan_ug_kth_se/Ed80j693XelDlu_Re0Pgm9UBjSTfhnjKaZ9gtT3pp58LUA?Download=1
unzip models_smplx_v1_1.zip
# Download vposer model
wget -O vposer_V1_0.zip https://kth-my.sharepoint.com/:u:/g/personal/qyuan_ug_kth_se/EcSSDMGKiVpAjlIIhvIOa30B0wGuM01JJl68hdJAQw1STw?Download=1
13351  [2023-07-29 17:02:48] unzip vposer_V1_0.zip

pip install scikit-learn scikit-image
pip uninstall pyglet
pip install pyglet==1.5.26

apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends         build-essential cmake git wget vim ffmpeg software-properties-common         python3-setuptools python3-dev python3-pip python3-tk cython         libx264-dev sudo pkg-config libyaml-dev libopencv-dev         libgoogle-glog-dev libboost-all-dev libhdf5-dev libatlas-base-dev         libopencv-dev protobuf-compiler libgoogle-glog-dev libboost-all-dev         libhdf5-dev libatlas-base-dev libprotobuf-dev zip unzip file ninja-build p7zip-full p7zip-rar         llvm-6.0 freeglut3 freeglut3-dev mesa-utils libegl1 libosmesa6-dev build-essential  libgl1-mesa-dev freeglut3-dev libglu1-mesa-dev

# Only cfg_files/fit_smplx_smplifyx.yaml works for now, other config files require PIXIE prior

#python3.7 smplifyx/main.py --cofig cfg_files/fit_smplx_combined_coco25.yaml data_folder /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case26_smplify-x-partial/ --output_folder /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case26_smplify-x-partial_results --visualize False --model_folder /workspace/models/smplx/ --vposer_ckpt /workspace/vposer_v1_0/ --use_gender_classifier False --gender='male' --interpenetration True --part_segm_fn smplx_parts_segm.pkl --save_vertices True --expose_results_directory /cephyr/users/yuanq/Alvis/content/inference_result.npz

#python3.7 smplifyx/main.py --config cfg_files/fit_smplx_smplifyx.yaml --data_folder /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case26_smplify-x-partial/ --output_folder /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case26_smplify-x-partial_results --visualize False --model_folder /workspace/models/ --vposer_ckpt /workspace/vposer_v1_0/ --use_gender_classifier False --gender='male' --interpenetration True --part_segm_fn smplx_parts_segm.pkl --save_vertices True

python3.7 smplifyx/main.py --config cfg_files/fit_smplx_smplifyx.yaml --data_folder /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case26_smplify-x-partial/ --output_folder /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case26_smplify-x-partial_results --visualize False --model_folder /workspace/models/ --vposer_ckpt /workspace/vposer_v1_0/ --use_gender_classifier False --gender='male' --interpenetration False --part_segm_fn smplx_parts_segm.pkl --save_vertices True --result_folder /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case26_smplify-x-partial_results
```
