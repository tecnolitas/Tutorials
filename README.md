# Instalar Kohya LoRA GUI en RunPod
Repositios Khoya interesante

Kohya SS Gui Repo : https://github.com/bmaltais/kohya_ss

Aqui estan los comandos para instalar Khoya en Runpod y los comandos para descargar los modelos desde [civitai](https://civitai.com)
### Modelos y recursos
Realistic Vision V2 Full model : https://huggingface.co/SG161222/Realistic_Vision_V2.0/resolve/main/Realistic_Vision_V2.0.safetensors

```bash
wget https://huggingface.co/SG161222/Realistic_Vision_V2.0/resolve/main/Realistic_Vision_V2.0.safetensors
```
RPG V4 Full model: https://huggingface.co/danbrown/RPG-v4/tree/main
```bash
wget https://huggingface.co/danbrown/RPG-v4/resolve/main/rpg-v4.safetensors
```
Best vae : https://huggingface.co/stabilityai/sd-vae-ft-mse-original/resolve/main/vae-ft-mse-840000-ema-pruned.ckpt
```bash
wget https://huggingface.co/stabilityai/sd-vae-ft-mse-original/resolve/main/vae-ft-mse-840000-ema-pruned.ckpt
```
## Comandos para terminal de runpod
```bash
git clone https://github.com/bmaltais/kohya_ss.git
```
```bash
cd kohya_ss
```
```bash
python3 -m venv venv
```
```bash
source venv/bin/activate
```

### Hay que instalar alguna dependencia

```bash
apt update
```
```bash
apt-get install python3.10-tk
```
```bash
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```
### Ejecutamos el script de instalación
```bash
./setup.sh -n
```

### Finalmente ejecutamos la aplicación
```bash
bash gui.sh --share
```

## Parametros para la pestaña de Technical parameters
|Parametro|Valor|
|--------------------------------|-----------------------|
| Train batch size               |          2            |
| Epoch                          |          1            |
| Save every epoch               |          1            |
| Caption extension              |        .txt           |
| Mixed precision                |        bf16           |
| Save precision                 |        bf16           |
| number of CPU threats per core |          2            |
| seed							 |        1234           |
| learning rate                  |        0.001          |
| LR scheduler                   |       constant        |
| LR warmup (% of steps)         |         10            |
| Cache laten                    |       marcado         |
| text encoder learning rate     |      0.00001          |
| unet learning rate             |        0.0001          |
| network rank                   |          128          |
| max resolution                 |       512,512         |
| stop text encoder training     |           0           |
| enable buckets                 |       marcado         |
| max resolution                 |       512,512         |
| max resolution                 |       512,512         |
|Advance configuration                                   |
| Use xformers                 |       desmarcado        |
| Skip clip               |       2        |
| Max num workers for DataLoader | 1 |

