# Quiz
## Autor: Samuel Parra
## Entrega
Para desplegar lo que se pide primero se descarga el proyecto desde GitHub con el comando:
```
git clone https://github.com/rparak/PyBullet_Industrial_Robotics_Gym.git
```
Luego se crea un entorno virtual en Conda ya que el autor lo recomienda para el proyecto:
```
conda create -n pybullet_env python=3.10
conda activate pybullet_env
```
También el autor puso los paquetes que se deben instalar:
```
Matplotlib
$ ../user_name> conda install -c conda-forge matplotlib

SciencePlots
$ ../user_name> conda install -c conda-forge scienceplots

PyBullet
$ ../user_name> conda install -c conda-forge pybullet

Pandas
$ ../user_name> conda install -c conda-forge pandas

SciPy
$ ../user_name> conda install -c conda-forge scipy

PyTorch, Torchvision, etc.
$ ../user_name> conda install pytorch::pytorch torchvision torchaudio -c pytorch
or 
$ ../user_name> conda install pytorch-nightly::pytorch torchvision torchaudio -c pytorch-nightly

Stable-Baselines3
$ ../user_name> conda install -c conda-forge stable-baselines3

Gymnasium
$ ../user_name> conda install -c conda-forge gymnasium
```
Después de instalar todos los paquetes uno por uno se intentó ejecutar el archivo ppal del proyecto:
```
python src/PyBullet/Configuration/Environment.py
```
Sin embargo, Durante la ejecución se detectó que el proyecto depende de un módulo externo llamado RoLE, el cual no está incluido en el repositorio ni disponible en los gestores de paquetes (pip o conda). Debido a esto, cloné el repositorio https://github.com/rparak/RoLE.git e intenté enlazarlo manualmente, pero, el código principal no logra importar sus clases, por lo que el entorno no puede inicializarse correctamente.

Aquí las pruebas:

<img width="1098" height="144" alt="image" src="https://github.com/user-attachments/assets/cbb25f1b-92f4-41c8-8961-527a4b230782" />\
\
En esta imagen, el error NameError: name 'HTM_Cls' is not defined ocurre porque el archivo principal (Environment.py) intenta usar la clase HTM_Cls, la cual debería ser importada desde el módulo RoLE.
Sin embargo, el entorno no reconoce ni puede importar dicho módulo, por lo que la clase no se define y el programa no se va a ejecutar, no se si el autor modificó los códigos pero intenté de todas las maneras y no pude desplegar el "Enviroment E1".


