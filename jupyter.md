INSTALACION DE ANACONDA3
-
    cd /tmp
    wget https://repo.continuum.io/archive/Anaconda3-5.3.1-Linux-x86_64.sh

    bash Anaconda3-2018.12-Linux-x86_64.sh

    Do you accept the license terms? [yes|no]
    [no] >>> yes

    [/root/anaconda3] >>> /usr/local/anaconda3

    Do you wish the installer to initialize Anaconda3
    in your /root/.bashrc ? [yes|no]
    [no] >>> yes

    source ~/.bashrc

    conda install python=3.5

    jupyter notebook --generate-config
    nano ~/.jupyter/jupyter_notebook_config.py
Y modificamos la línea de esta forma:

    c.NotebookApp.allow_root=True
    jupyter notebook password

JUNTAR APACHE SPARK Y JUPYTER:
-
    nano ~/.bashrc
    export PYSPARK_DRIVER_PYTHON=jupyter
    export PYSPARK_DRIVER_PYTHON_OPTS='notebook'

    source ~/.bashrc
