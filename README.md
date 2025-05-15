# Python environment managers on Surf Research Cloud

[![Static Badge](https://img.shields.io/badge/Python-black?style=flat-square&logo=python&logoColor=blue&labelColor=gray&color=yellow)](https://www.python.org/)
[![Static Badge](https://img.shields.io/badge/jupyter-blue?style=flat-square&logo=jupyter&logoColor=white&labelColor=gray&color=orange)](https://jupyter.org/)
[![Static Badge](https://img.shields.io/badge/MIT%20License%20-blue?style=flat-square)](https://github.com/UtrechtUniversity/src-jupyter-workshop-template/blob/main/LICENSE)

This repository contains a reproducible example project for demonstrating how to work with different Python environment managing tools on SURF Research Cloud. The repository contains multiple files with the same dependencies following different conventions for the different environment management tools used.

Environment managing tools make it possible to install exactly the packages that where use for developing code on a new computer (e.g. a Research Cloud workspace) with one (or a few) commands. If you would like to learn more about setting up a reproducible project, the workshop [Best Practices for Writing Reproducible code](https://www.uu.nl/en/research/research-data-management/training-workshops/best-practices-for-writing-reproducible-code) might be interesting for you.

The Jupyter notebook in this Repository was originally created by [Aristotelis Kandylas](https://github.com/AristotleKandylas) as part of a [Python for GIS workshop](https://github.com/UtrechtUniversity/gis-python-power).

## Python tools

The environment managers used are:

- [`uv`](https://docs.astral.sh/uv/) (recommended: easy to use, lightning fast, and lockfiles)
- [`pyenv`](https://github.com/pyenv/pyenv)
- [`conda`](https://docs.conda.io/en/latest/)

The main Python libraries used are:

- `geopandas`
- `matplotlib`
- `pandas`
- `shapely`
- `fiona`

## Scenario 1: Workspace: Python Workbench Desktop 

### Step 1: Clone the repository
Open a terminal (under Applications, top left of the screen).
Navigate to your storage volume (if you didn't attach a storage volume, scratch folder is also fine)

In the terminal window, type:
```
ls
cd data
ls
```
Check the exact name of your storage volume in the output in the terminal. It should be similar to the name you entered when creating the storage.

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

- Open VSCodium (Applications > Development > VSCodium)
- Open the folder of the cloned github repo
- Open notebooks/Vectors.ipynb
- Install the required extensions (will be asked to you)
- Select python interpreter (.venv (or geo-kernel in case of conda environment)
- Click: Run all

### (Optional) Step 4: Run this Notebook as a job with `run_and_pause`

The Notebook in this project is executed very fast. Imagine that you have a notebook that takes hours to run. While it should be able to do this exactly as described above, the more robust and recommended way is to run such a notebook as a 'background job' with `run_and_pause` or `nohup`. Find instructions on how to do this in [this manual](https://utrechtuniversity.github.io/vre-docs/docs/manuals/long-jobs.html).

### (Optional) Step 5: Transfer your output data to cloud storage directly
If you have a [Surfdrive](surfdrive.surf.nl)-, Researchdrive- of Yoda account, you can transfer your output data there directly. Use the [manuals on our documentation website](https://utrechtuniversity.github.io/vre-docs/docs/manuals.html) to transfer your data there directly. 
> For Onedrive you could click Applications and then Firefox and upload your data using the web portal. This is also possible for SURFdrive and Yoda, but we would recommend using the commend line methods above for reliability and automation.



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
Check the exact name of your storage volume in the output in the terminal

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

## Step 3: Create Jupyter kernel

Run the following command to create a new kernel that you can use for Jupyter notebooks:
```
python -m ipykernel install --user --name geo-kernel --display-name "Geo kernel" 
```

## Step 4: Run the `Vectors.ipynb` Jupyter notebook
In the filebrowser on the left, navigate to the cloned repository (`src-python-example`), and then to the notebooks folder.
Double click the `Vectors.ipynb` notebook to open it. 
In the top right corner, select the `Geo kernel` and then the fast forward button to run all cells of the notebook.

### (Optional) Step 5: Run this Notebook as a job

The Notebook in this project is executed very fast. Imagine that you have a notebook that takes hours to run. While it should be able to do this exactly as described above, the more robust and recommended way is to run such a notebook as a 'background job' with `nohup`. Find instructions on how to do this in [Method 2 in this manual](https://utrechtuniversity.github.io/vre-docs/docs/manuals/long-jobs.html#method-2-using-nohup).

### (Optional) Step 6: Transfer your output data to cloud storage directly
If you have a [Surfdrive](surfdrive.surf.nl)-, Researchdrive- of Yoda account, you can transfer your output data there directly. Use the [manuals on our documentation website](https://utrechtuniversity.github.io/vre-docs/docs/manuals.html) to transfer your data there directly. 
> In theory this is also possible for OneDrive but this is not straightforward because you need web browser to login to Onedrive. The easiest way is to download data to your laptop first and then upload it to Onedrive.


## Contact

[UU Research Engineering team](https://www.uu.nl/research-engineering)
