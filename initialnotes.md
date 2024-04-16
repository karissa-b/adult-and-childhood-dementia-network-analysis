# First crack at getting network to work. 

## Genesets 

The genes which are associated with childhood dementia were obtained from the CDI knowledgebase (Accessed on 12/4/24). 

There are 236 genes in the database currently. The download wasnt working but luckily the copy paste was OK. 

For adult dementia, I found a recent meta-analysis of AD GWAS genes (From supp table 1): 
https://www.thelancet.com/journals/ebiom/article/PIIS2352-3964(23)00076-2/fulltext


## conda env setup 

`conda create -n netcoloc`

`conda activate netcoloc`

`conda install pip`

`pip install netcoloc`

`git clone --branch python3 https://github.com/idekerlab/ddot.git` 

`cd ddot ` 

`python setup.py bdist_wheel `

`pip install dist/ddot*py3*whl`

this failed. I think its a compatability between python versions. 

So for this conda env, I will run python3.19 (as the github repo says this ddot will only work < python3.10) 

`conda install python=3.7`
pip install netcoloc
`python --version`
> Python 3.9.19

this hasnt overly worked. I think its because i cant install ddot, as python3.6 is super old and doesnt appear to be supported on M series macs. 

The package tulip seems to be the problem here. I downloaded latest version from here: 
https://sourceforge.net/projects/auber


conda install python
pip install 

export PYTHONPATH="/Applications/Tulip-5.7.4.app/Contents/lib/python:$PYTHONPATH"

export DYLD_LIBRARY_PATH="/Applications/Tulip-5.7.4.app/Contents/lib:$DYLD_LIBRARY_PATH"  # Replace with your actual directory



Try a python virtual env. maybe conda is the problem

also try  on my intel MBP. 

```
# create the conda env
conda create --name "netcoloc" python=3.9
conda activate netcoloc

conda install -y -c conda-forge python-igraph
conda install -y libiconv pandas numpy scipy networkx>=2.0

pip install tulip-python
pip install ndex-dev

# was in the ddot dir
pip install . 

pip install cdapsutil
```

This has worked!!!! 
But its super slow. 

Im going to try on deepthought using jupyterhub

```
conda create --name netcoloc2 python=3.9
conda activate netcoloc2

# check python version:
python --version
# > Python 3.9.17

# ~~ install packages ~~ 
# for jupyter on deepthought. 
python3 -m pip install cm-jupyter-eg-kernel-wlm bash-kernel
conda install ipython ipython_genutils


conda install -y -c conda-forge python-igraph
conda install -y libiconv
conda install -y pandas numpy scipy networkx>=2.0

pip install tulip-python

pip install netcoloc
```


