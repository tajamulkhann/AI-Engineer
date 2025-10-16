# Conda Commands Cheat Sheet (VS Code)

| Command                                  | Purpose                                              |
|------------------------------------------|------------------------------------------------------|
| `conda --version`                        | Check Conda version                                  |
| `conda create -n env_name python=3.10`   | Create new environment with Python version           |
| `conda env list`                         | List all environments                                |
| `conda activate env_name`                | Activate an environment                              |
| `conda deactivate`                       | Deactivate current environment                       |
| `conda install package_name`             | Install a package in the active environment          |
| `conda install -r requirements.txt`      | Install requirements.txt                             |
| `conda install -c channel package_name`  | Install package from specific channel (e.g., conda-forge) |
| `conda update conda`                     | Update Conda itself                                  |
| `conda update package_name`              | Update a specific package                            |
| `conda list`                             | List installed packages in active environment        |
| `conda remove package_name`              | Remove a package                                     |
| `conda remove -n env_name --all`         | Delete an environment                                |
| `conda env export > environment.yml`     | Export environment to `.yml` file                    |
| `conda env create -f environment.yml`    | Create environment from `.yml` file                  |
| `conda clean --all`                      | Remove unused packages and cache                     |

## Difference between -n and -p

| Command                                    | Description                         | Environment Location     | Activation Command            |
| ------------------------------------------ | ----------------------------------- | ------------------------ | ----------------------------- |
| `conda create -n myenv python=3.11`        | Creates env with name `myenv`       | `~/anaconda3/envs/myenv` | `conda activate myenv`        |
| `conda create -p /path/to/env python=3.11` | Creates env at specific folder path | `/path/to/env`           | `conda activate /path/to/env` |
