
tags: #jupyter #virtual-environment #python #pip #conda
After creating virtual environment,

Install ipykernel:

```terminal
pip install --user ipykernel
```

add virtual environment to kernel:

```terminal
python -m ipykernel install --user --name=myenv
```

Add jupyter:

```terminal
pip install jupyter
```
