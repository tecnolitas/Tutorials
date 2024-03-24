# Tutorial para instalar Kohya LoRA en RunPod-Ultima version
* El tutorial utiliza el Archivo de configuración .json utilizado

## Scritp para descargar modelos y VAE en el nodo de Runpod

# Si vas a entrenar modelos con Stable Diffusion 1.5
* Descargue el archivo txt adjunto y elimina la extensión txt
+ * [Prueba1.json.txt] https://github.com/tecnolitas/Tutorials/blob/main/prueba.json.txt

# Si vas a entrenar modelos con Stable Diffusion XL
 


Realistic Vision V5.1 
```
wget https://huggingface.co/SG161222/Realistic_Vision_V5.1_noVAE/resolve/main/Realistic_Vision_V5.1.safetensors
```

SD 1.5 Best VAE
```
wget https://huggingface.co/stabilityai/sd-vae-ft-mse-original/resolve/main/vae-ft-mse-840000-ema-pruned.ckpt
```

## Scritp para descargar modelos y VAE en el nodo de Runpod para SD XL

MODELO BASE SD XL
```
wget https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/blob/main/sd_xl_base_1.0.safetensors
```

SDXL Best VAE
```
wget https://huggingface.co/stabilityai/sdxl-vae/resolve/main/sdxl_vae.safetensors
```

## Cómo instalar Kohya GUI en RunPod

* Selecciona stable-diffusion:web-ui   --> runpod/stable-diffusion:web-ui-10.2.1

* Haz que el tamaño del disco contenedor sea de al menos 15 GB
  
El proceso completo de instalación puede llevar facilmente 15-20 minutos

```
apt update
```

```
apt-get install python3.10-tk
```

```
cd /workspace
```

```
git clone https://github.com/bmaltais/kohya_ss.git
```

```
cd kohya_ss
```

```
python3 -m venv venv
```

```
source venv/bin/activate
```

```
pip install fastapi==0.99.1
```

```
./setup.sh -n
```
### Si aparece este problema cuando termina la ejecucion de los comandos

Traceback (most recent call last):
  File "/workspace/kohya_ss/setup/validate_requirements.py", line 19, in <module>
    from library.custom_logging import setup_logging
  File "/workspace/kohya_ss/library/custom_logging.py", line 6, in <module>
    from rich.theme import Theme
ModuleNotFoundError: No module named 'rich'

### ejecutar este comando
```
pip install rich

```
### Si aparece este problema

Could not automatically configure accelerate. Please manually configure accelerate with the option in the menu or with: accelerate config.          

### Ejecutar este comando
```
accelerate config
```


## Como ejecutarlo despues de la instalación

* Iniciar un nuevo terminal
* Copie y pegue el código siguiente
* Es posible que tenga que pulsar Intro dos veces después de copiar y pegar.

```
apt update
yes | apt-get install python3.10-tk
fuser -k 7860/tcp
cd /workspace/kohya_ss
source venv/bin/activate
pip install fastapi==0.99.1
bash gui.sh --share --headless
```

## Cómo Matar la Instancia de la Interfaz Web de Automatic1111 Antes del Entrenamiento e Iniciar la Interfaz Web Manualmente

Para eliminar la instancia Automatic1111 Web UI
```
fuser -k 3000/tcp
```

Para iniciar de nuevo la instancia Automatic1111 Web UI
```
cd /workspace/stable-diffusion-webui
python relauncher.py
```
