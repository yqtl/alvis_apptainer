 2549  [2022-12-09 18:57:26] apptainer build cliff.sif nvcr_io_pytorch_19.12-py3.def 
 2791  [2022-12-10 11:23:56] apptainer build cliff_post.sif post.def 
 2856  [2022-12-10 19:55:13] apptainer shell --fakeroot --writable-tmpfs cliff_post.sif 
