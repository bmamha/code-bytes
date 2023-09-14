#python #conda 


### to CREATE
```bash
conda create -n myenv python
```

### to activate

```terminal
conda activate project-environment
```


### to  check available enivronments 

```terminal
$ conda env list    
$ conda info --envs 
```


### to create environment in a specific folder

```bash
conda create --prefix ./envs jupyterlab=3.2 matplotlib=3.5 numpy=1.21
```

### to create a requirement (spec list) file from a conda environment

```bash
conda list --explicit > spec-file.txt
```


### to create a conda environment from a specific file

```bash
conda create --name myenv --file spec-file.txt
```

### Exporting using yml file

```bash
conda env export > environment.yml
```


only the packages I chose

```bash
conda env export --from-history
```


### updating an environment

```bash
$ conda env update --prefix ./env --file environment.yml  --prune
```

### Create an environment from environment.yml file
```bash
conda env create -f environment.yml
```