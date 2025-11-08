# Quiz
## Autor: Samuel Parra
## Entrega
Para desplegar lo que se pide primero se descarga el proyecto desde GitHub con el comando:
```
git clone https://github.com/rparak/PyBullet_Industrial_Robotics_Gym.git
```
Y se entra a la carpeta con:
```
cd PyBullet_Industrial_Robotics_Gym
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

Cabe recalcar que también se intentó desplegar con Docker pero el resultado es el mismo.
Para Docker al proceso se le agrega que se crea un archivo Dockerfile con
```
nano Dockerfile
```
Y se pega lo siguiente:
```
# Imagen base con Python 3.10
FROM python:3.10-slim

# Instalar dependencias del sistema
RUN apt-get update && apt-get install -y \
    git \
    python3-tk \
    xvfb \
    && rm -rf /var/lib/apt/lists/*

# Crear el directorio de trabajo
WORKDIR /app

# Copiar todo el código al contenedor
COPY . /app

# Instalar dependencias del proyecto
RUN pip install --upgrade pip
RUN pip install -r requirements.txt || true

# Comando por defecto
CMD ["python", "src/PyBullet/Configuration/Environment.py"]
```
Luego, se construye la imagen Docker:
```
docker build -t pybullet-gym .
```
Y se ejecuta el contenedor:
```
docker run -it --rm pybullet-gym
```
Pero el resultado fue el mismo...

<img width="1109" height="200" alt="image" src="https://github.com/user-attachments/assets/98b882d8-2189-4be8-a988-f9cf768e2bb4" />
<img width="1111" height="121" alt="image" src="https://github.com/user-attachments/assets/5e68a214-6878-4155-943c-0884c4301889" />
<img width="937" height="192" alt="image" src="https://github.com/user-attachments/assets/1bdcd7d1-3b64-4b7a-9e15-3ad26b195256" />




