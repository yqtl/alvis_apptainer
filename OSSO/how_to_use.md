OSSO.def cannot directly build due to shell environment, dirty fix is to build OSSO.sif using nvcr_io_pytorch_19.12-py3.def, then from OSSO.sif build with OSSO_post.def.
 3250  [2022-12-12 18:57:34] . /opt/conda/etc/profile.d/conda.sh
 3251  [2022-12-12 18:57:39] conda activate OSSO
 3255  [2022-12-12 18:57:55] cd /workspace/
 3257  [2022-12-12 18:57:58] cd OSSO/
 3258  [2022-12-12 18:57:59] source osso_venv/bin/activate
 3261  [2022-12-12 18:59:43] python main.py  --mesh_input /mimer/NOBACKUP/groups/snic2022-22-770/osso_model/female_50th_162cm_62kg_50y_no_mask.obj --gender female -D -v
