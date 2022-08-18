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
