Build from preprocess_blending.def first, which installs jupyter and mmpose.


Start jupyter container, under Alvis env:
    container=xxx.sif
    apptainer exec --nv $container jupyter notebook --config="${CONFIG_FILE}"

Go to forked version of smplify-x-partial ipynb notebook.
Do MMpose prediction, then blend with openpose(seperate predict).


Then build smplify-x-partial.def for smplx prediction.