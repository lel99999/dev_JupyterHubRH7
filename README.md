# dev_JupyterHubRH7
JupyterHub and JupyterLab Workspace and Notes

##### Notes
- Jupyter Notebook Commands: <br/>
  `$jupyter notebook --no-browser --port=<port number>` <br/>

- Install jupyterhub, jupyterlab, ipywidgets <br/>
  ```
  python3 -m venv /opt/jupyterhub/
  /opt/jupyterhub/bin/python3 -m pip install wheel
  /opt/jupyterhub/bin/python3 -m pip install --upgrade pip    ## Fixes RustExtention Error
  /opt/jupyterhub/bin/python3 -m pip install jupyterhub jupyterlab
  /opt/jupyterhub/bin/python3 -m pip install ipywidgets
  ```
- Generate Config <br/>
  ```
  $cd /opt/jupyterhub/etc/jupyterhub
  $/opt/jupyterhub/bin/jupyterhub --generate-config
  ```

- Install nodejs, npm <br/>
  ```
  $sudo yum -y install nodejs npm
  ```

#### Adding Kernels
- Custom Virtualenv
  ```
  ## activate virtualenv
  $source custom-venv/bin/activate
  
  ## install jupyter in the virtualven
  $(custom-venv)$pip install jupyter
  
  ## add virtualvenv as jupyter kernel
  (custom-venv)$ipython kernel install --name "custom-venv" --user
  ```
- Spark Kernel (prerequisite: Java and local Spark installation)
  ```
  $pip install jupyter
  $pip install --upgrade toree
  $jupyter toree install --user --spark_home=/<path>/spark-2.4.8-bin-hadoop2.7
  $jupyter notebook  ## select Apache Toree -Scala
  ```
