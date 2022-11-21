# dev_JupyterHubRH7
JupyterHub and JupyterLab Workspace and Notes

##### Notes
- Jupyter Notebook Commands: <br/>
  `$jupyter notebook --no-browser --port=<port number>` <br/>
  
  Run shell commands in notebook: <br/>
  `!ls -altr .` <br/>

- Install jupyterhub, jupyterlab, ipywidgets <br/>
  ```
  $sudo python3 -m venv /opt/jupyterhub/
  /opt/jupyterhub/bin/python3 -m pip install wheel
  /opt/jupyterhub/bin/python3 -m pip install --upgrade pip    ## Fixes RustExtention Error
  /opt/jupyterhub/bin/python3 -m pip install jupyterhub jupyterlab
  /opt/jupyterhub/bin/python3 -m pip install ipywidgets
  ```
- Generate Config <br/>
  ```
  $cd /opt/jupyterhub/etc/jupyterhub
  $sudo /opt/jupyterhub/bin/jupyterhub --generate-config
  ```

- Install nodejs, npm <br/>
  ```
  $sudo yum -y install nodejs npm
  ```

- Install configurable-http-proxy - If Error: Require that node >= 12+, (v16.17.0) <br/>
  ```
  #npm install -g "configurable-http-proxy
  ```

- Configure configurable-http-proxy <br/>
  ```
  #ln -s /usr/local/bin/configurable-http-proxy /<path>/bin/configurable-http-proxy
  ```

- Yarn Package Manager Example
  ```
  $yarn add jupyter-leaflet
  ```

- JupyterLab Package Manager <br/>
  ```
  $jlpm add @lumino/widgets
  $jlpm add @jupyterlab/outputarea
  ```

#### Extension Manager (Issues/Notes)
- Permission denied - 500: Internal Error
  Check the permissions on the shared location i.e. /etc/jupyterhub/shared <br/> 
  
#### Adding Kernels
- Custom Virtualenv
  ```
  ## activate virtualenv
  $source custom-venv/bin/activate
  
  ## install jupyter in the virtualenv
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
- Scala Kernel
  ```
  ## Download almond and scala libs (coursier is a scala tool to install almond)
  $curl -Lo coursier https://git.io/coursier-cli && chmod +x coursier
  
  ## update/replace scala and almond versions if need be
  $ ./coursier bootstrap \
    -r jitpack \
    -i user -I user:sh.almond:scala-kernel-api_2.12.11:0.10.0 \
    sh.almond:scala-kernel_2.12.11:0.10.0 \
    -o almond
    
  ## install scala kernel in jupyter
  $./almond --install --id scala_2_12_11  --display-name "Scala 2.12.11"
  
  ## open jupyter notebook and select Scala kernel
  $jupyter notebook
  ```
- List kernels
  `$jupyter kernelspec list` <br/>
  
- Remove kernel
  `$jupyter kernelspec remove <kernel_name>` <br/>

- Change kernel name
  ```
  ## use $juypter kernelspec list to see folder location of kernel
  ## edit kernel.json, update/modify "display name" of kernel
  ```
- Adding R to Jupyter
  ```
  ## Install jupyter client
  $conda install -c anaconda jupytr_client
  
  ## Install IR Kernel
  $conda install -c r r-irkernel
  
  ## Run 3 Commands in R
  >install.packages("devtools")
  >devtools::install_github("IRkernel/IRkernel")
  >IRKernel::installspec()
  
  ```

#### Proxy using Apache
- Proxy user login error/SSL error
  ```
  #Require valid-user
  Require all granted
  #Require user <user1> <user2>
  ```

#### Jupyterhub Errors
- Jupyterlab-git server extension<br/>
  ![https://github.com/lel99999/dev_JupyterHubRH7/blob/main/jupyterlab-git_error-01.PNG](https://github.com/lel99999/dev_JupyterHubRH7/blob/main/jupyterlab-git_error-01.PNG) <br/>
  Fix: <br/>
  ```
  !pip install --upgrade jupyterlab-git
  ```
