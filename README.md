# Python environment managers on Surf Research Cloud

[![Static Badge](https://img.shields.io/badge/Python-black?style=flat-square&logo=python&logoColor=blue&labelColor=gray&color=yellow)](https://www.python.org/)
[![Static Badge](https://img.shields.io/badge/jupyter-blue?style=flat-square&logo=jupyter&logoColor=white&labelColor=gray&color=orange)](https://jupyter.org/)
[![Static Badge](https://img.shields.io/badge/MIT%20License%20-blue?style=flat-square)](https://github.com/UtrechtUniversity/src-jupyter-workshop-template/blob/main/LICENSE)

This repository contains a reproducible example project for demonstrating how to work with different Python environment managing tools on SURF Research Cloud. The repository contains multiple files with the same dependencies following different conventions for the different environment management tools used.

The Jupyter notebook in this Repository was originally created by [Aristotelis Kandylas](https://github.com/AristotleKandylas) as part of a [Python for GIS workshop](https://github.com/UtrechtUniversity/gis-python-power).

## Python tools

The environment managers used are:

- `uv`
- `pyenv`
- `conda`

The main Python libraries used are:

- `geopandas`
- `matplotlib`
- `pandas`
- `shapely`
- `fiona`

## Scenario 1: Python Workbench Desktop

### Step 1: Clone the repository, save it on storage

We will save this example repository, which also contains the data, on the workspace's permanent storage data. In many real-life cases, your data and code will live in separate locations. In that case, it makes sense to save the data, but not the code, on a permanent storage unit.

Steps:

- Open a terminal.
- You will find your storage unit in the `/data` folder, so go there: `cd /data`
- `ls` to find out the exact name of your storage unit.
  * it will be something like `my_storage`, depending on the name you provided when creating the unit.
- Enter the storage directory with: `cd my_storage`.

Now:

```
git clone https://github.com/UtrechtUniversity/src-python-example.git
cd src-python-example/
```

### Step 2: Create Environment 

#### Option 1: `uv`
##### Option 1a: From `pyproject.toml` and lockfile `uv.lock`

```
uv sync
source .venv/bin/activate
```

##### Option 1b: From `requirements.txt`

```
uv venv --python 3.10
source .venv/bin/activate
uv pip install -r requirements.txt
```

#### Environment option 2: `pyenv` with requirements.txt

```
pyenv install 3.10
pyenv exec python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

#### Environment option 3: `conda` with environment.yml

```
conda init
conda env create --file=environment.yml
conda activate geo-kernel
```

### Step 3: Run the the Jupyter notebook in VSCodium

- Open VSCodium (Applications > Development > VSCodium)
- Open the folder of the cloned github repo (under `/data/...`)
- Open notebooks/Vectors.ipynb
- Install the required extensions (will be asked to you)
- Select python interpreter (`.venv` (or `geo-kernel` in case of conda environment)
- Click: Run all

## Contact

[UU Research Engineering team](https://www.uu.nl/research-engineering)
