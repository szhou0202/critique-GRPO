first, `module load miniconda` and `module load CUDA`. 

to set up the env properly, i had to first create the conda env without installing the pip dependencies. then i had to activate the env, and manually pip install torch and numpy. then i could run `pip install -r training_requirements.txt`. 

this is because flash_attn relies on torch and numpy, but the modules don't exist until the entire pip installation process finishes successfully. so we have to install those first, then install the rest. 

this is located in the scratch folder because the scratch folder has a higher disk utilization cap. the conda env should be placed in the scratch folder to take advantage of this cap, otherwise we will keep getting the disk utilization cap error. 

also it looks like the versioning in the .yml and .txt files might be cooked, prevented me from installing sglang, which is part of the verl installation it seems. 

NOTE: xgrammar==0.1.18 works with sglang[all]==0.4.6.post4! so just downgrade xgrammar after installing sglang[all]==0.4.6.post4 and that should resolve all dependency conflicts. 

i also think we have to load CUDA/12.6 for some sort of compatibility issue as well

NOTE: i really REALLY dont know if i should be running the install_vllm_sglang_mcore.sh script in verl/ !!!!!! because it KEEPS messing up dependencies!!!!! by a lot!!!!

because of resource constraints, change num gpus and num workers to 2 each
