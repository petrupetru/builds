# Builds

To run this project you will need a python enviroment  
For python 3.7 use branch "2.0-verified" of ml_agents or "release_20" for newer version  
Change number from build4 to use a different build version  
```
# Cloning the ml-agents repo.(branch depending on python version)
!git clone --branch release_20 https://github.com/Unity-Technologies/ml-agents.git  


# Installing the ml-agents from the repo.
!pip install -e ml-agents/ml-agents-envs/  
!pip install -e ml-agents/ml-agents/  

# Pytorch
!pip3 install torch~=1.7.1 -f https://download.pytorch.org/whl/torch_stable.html

# Check if training works
!mlagents-learn --help


#Get the env build
import shutil
shutil.rmtree('builds')
!git clone https://github.com/petrupetru/builds.git


# Set the permissions
!chmod -R 755 builds/build4/build4.x86_64
!chmod -R 755 builds/build4/UnityPlayer.so
!ls -l builds/build4

# Set the Environment name
env_name = "builds/build4/build4.x86_64"



# required: --run-id=, --env=, --no-graphics       
# optional --num-envs=, --initialize-from=, --resume
# run-id must be different for every training session if you don't use the --resume argument
# resume only works if the run-id was used for train session that was interrupted
# initialize-from takes a value of a previews run-id as its value if used(different from resume, training starts from step 0)
!mlagents-learn config.yaml --run-id=403 --env=$env_name --no-graphics --num-envs=2 --initialize-from=401 > log.txt


# Optional
%tensorboard --logdir Assets/results
```
