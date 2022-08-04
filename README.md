# dev_JupyterHubRH7
JupyterHub and JupyterLab Workspace and Notes

##### Notes
- Jupyter Notebook Commands:
  `$jupyter notebook --no-browser --port=<port number>` <br/>

- Install jupyterhub, jupyterlab, ipywidgets
  ```
  python3 -m venv /opt/jupyterhub/
  /opt/jupyterhub/bin/python3 -m pip install wheel
  /opt/jupyterhub/bin/python3 -m pip install --upgrade pip    ## Fixes RustExtention Error
  /opt/jupyterhub/bin/python3 -m pip install jupyterhub jupyterlab
  /opt/jupyterhub/bin/python3 -m pip install ipywidgets
  ```

- Install nodejs, npm
  ```
  $sudo yum -y install nodejs npm
  ```
