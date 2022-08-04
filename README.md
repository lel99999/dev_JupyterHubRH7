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
