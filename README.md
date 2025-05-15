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

## Scenario 1: Workspace: Python Workbench Desktop 

### Step 1: Clone the repository
Open a terminal
Navigate to your storage volume (if you didn't attach a storage volume, scratch folder is also fine)

In the terminal window, type:
```
cd data
ls
```
Check the exact name of your storage volume in the output in the terminl

```
cd <the name of your storage volume>
```
Then clone this github repository:

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

- Open VSCodium
- Open the folder of the cloned github repo
- Open notebooks/Vectors.ipynb
- Install the required extensions (will be asked to you)
- Select python interpreter (.venv (or geo-kernel in case of conda environment)
- Click: Run all

## Scenario 2: Workspace: Jupyter Notebook

### Step 1: Clone the example GitHub repository

Open a terminal by clicking the blue button with '+' sign.

Navigate to your storage volume (if you didn't attach a storage volume, scratch folder is also fine)

In the newly opened terminal window, type:
```
ls
cd data
ls
```
Check the exact name of your storage volume in the output in the terminl

```
cd <the name of your storage volume>
```
Then clone this github repository:

```
git clone https://github.com/UtrechtUniversity/src-python-example.git
cd src-python-example/
```

## Step 2: Create environment

### Option 1: `uv` 

Install `uv`
```
curl -LsSf https://astral.sh/uv/install.sh | sh
```
The terminal will tell you to close the terminal and open a new one.

After opening a new terminal, make sure you are in the `src-python-example` folder and create and activate the virtual environment:

```
uv sync
source .venv/bin/activate
```

### Option 2: `conda` 

Initialize conda
```
/etc/miniconda/bin/conda init
```
The terminal will tell you to close the terminal and open a new one.

After opening a new terminal, make sure you are in the `src-python-example` folder and create and activate the virtual environment:

```
conda env create --file=environment.yml
conda activate geo-kernel
```

## Step 4: Create Jupyter kernel

Run the following command to create a new kernel that you can use for Jupyter notebooks:
```
python -m ipykernel install --user --name geo-kernel --display-name "Geo kernel" 
```

## Step 5: Run the `Vectors.ipynb` Jupyter notebook
In the filebrowser on the left, navigate to the cloned repository (`src-python-example`), and then to the notebooks folder.
Double click the `Vectors.ipynb` notebook to open it. 
In the top right corner, select the `Geo kernel` and then the fast forward button to run all cells of the notebook.

### (Optional) Step 5: Run this Notebook as a job

The Notebook in this project is executed very fast. Imagine that you have a notebook that takes hours to run. While it should be able to do this exactly as described above, the more robust and recommended way is to run such a notebook as a 'background job' with `nohup`. Find instructions on how to do this in [Method 2 in this manual](https://utrechtuniversity.github.io/vre-docs/docs/manuals/long-jobs.html#method-2-using-nohup).

## Contact

[UU Research Engineering team](https://www.uu.nl/research-engineering)
