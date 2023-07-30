11545  [2023-07-23 00:09:32] apptainer build smplifyx.sif smplifyx.def
11546  [2023-07-23 00:25:31] cd /workspace/human_body_prior/
11547  [2023-07-23 00:25:40] vim setup.py
11548  [2023-07-23 00:25:55] python setup.py install
11549  [2023-07-23 00:26:27] pip install opencv-python==4.5.5.64
11550  [2023-07-23 00:26:35] python setup.py install
11551  [2023-07-23 00:26:55] cd ../smplify-x/
11552  [2023-07-23 00:27:00] cp /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case45/out3029_cropped_vibe/out3029_cropped_resize.jpg data/images/
11553  [2023-07-23 00:27:04] cp /mimer/NOBACKUP/groups/snic2022-22-770/Frontiers_framework/Case45/out3029_cropped_vibe/out3029_cropped_resize_keypoints.json data/keypoints/
11554  [2023-07-23 00:27:09] xvfb-run -s "-screen 0 800x600x24" python smplifyx/main.py --config cfg_files/fit_smplx.yaml --data_folder data/ --output_folder ./ --visualize="True" --model_folder models/ --vposer_ckpt ../vposer_v1_0/ --part_segm_fn smplx_parts_segm.pkl --use_vposer True