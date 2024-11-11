# DropletTracking: DrTrack

Data Science Lab 2023 at ETH Zurich. Challenge: Tracking Droplets in Microfluidic Devices.
Complete Analysis Pipeline for Droplet Tracking, Training, Simulation and bio-assay read-out.

## Team
| Name                 | Email               | Github                                        |
| -------------------- |---------------------| --------------------------------------------- |
| S. Gutjahr | sgutjahr@ethz.ch    | [svenlg](https://github.com/svenlg) |
| T. Hungerland     | thungerland@ethz.ch | [thungerland](https://github.com/thungerland)         |
| R. Danis        | rdanis@ethz.ch      | [richdanis](https://github.com/richdanis)     |
| W. Ormaniec        | wormaniec@ethz.ch   | [werkaaa](https://github.com/werkaaa)     |
| M. Vollenweider        | michavol@ethz.ch    | [michavol](https://github.com/michavol)     |
| L. Schlotheuber        | lschlotheube@ethz.ch    | [ls154](https://github.com/ls154)     |



## Run Main Pipeline
1. Save the ```.nd2``` file in a folder in the root called ```data/01_raw```
2. Set the ```experiment_name``` and ```raw_image``` variables in the ```conf/config_track_droplets.yaml``` file.

    Set any other variables according to your ```.nd2``` file
3. Set up the environment by running: 
    ```
    pip install -r requirements.txt
    ```
4. To run the full pipeline, run from the root of the folder:
    ```
    python src/track_droplets.py
    ```
    You can run only the setup part of the python script to setup the directory structure automatically.
5. To run the evaluation pipeline, configure your experiment in src/conf/config_evaluation.yaml and run:
    ```
    python src/evaluate_tracking.py
    ```

## Setup for Linux
- First create a python environment, using the requirements.txt
```python -m venv env_name```

- Activate the environment by running (in the directory of env_name):
```source env_name/bin/activate```

- Then install the requirements.txt (in the directory of requirements.txt):
```pip install -r requirements.txt```

## Download of Necessary Data
- To run the track_droplets.py, make sure to have saved a .nd2 image in data/01_raw.
Check out the config_track_droplets_.yaml in src/conf for further settings.

- To run evaluate_tracking.py, make sure to have installed the paired patch data (link to download). 
Store it inside the evaluation/03_features folder. Check out the config_evaluation.yaml in src/conf for further settings.


The model stored under checkpoints was trained on droplets containing cells only.
You can download a model trained on droplets without cells from here:
https://www.polybox.ethz.ch/index.php/s/a1N5XC2lZNmccvf

## Setup GPU (might not work on your machine)
1. For GPU support make sure to do the following
2. Install the NVidia cuda-toolbox for cuda 11.8 on the machine
3. Create a conda environment with 3.11.7
4. ```pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118```
5. ```pip install ott-jax```
6. ```pip install --upgrade "jax[cuda11_pip]" -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html```

