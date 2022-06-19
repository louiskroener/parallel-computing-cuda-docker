# GPU Virtualisierung (mit Docker)
## Installation (WSL 2 Ubuntu)
- WSL2 Ubuntu aufsetzen (siehe Microsoft Docs)
- Docker Desktop installieren und Docker für WSL2 Ubuntu aktivieren
- gcc installieren (falls noch nicht vorhanden)
- https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=runfile_local
- Cuda installieren mit präferierter Methode (s. Link)

``nvidia-smi``

![image](https://user-images.githubusercontent.com/107040049/174431490-c068eaca-9666-4589-9aaf-bf54b31f6e02.png)
- check ob cuda über container läuft 

``docker run --rm --gpus all nvidia/cuda:11.7.0-runtime-ubuntu20.04 nvidia-smi``
![image](https://user-images.githubusercontent.com/107040049/174431678-51bece42-ddf9-4efd-96c8-06c83837c9cc.png)
- GPU Benchmark

``sudo docker run --gpus all nvcr.io/nvidia/k8s/cuda-sample:nbody nbody -gpu -benchmark``
![image](https://user-images.githubusercontent.com/107040049/174431593-f165dc29-406c-46bb-8bf8-5404edd711a6.png)

## Praktische Beispiele
### Was lässt uns die Runtime konfigurieren
- --gpu Flag zum steuern mit welche GPU Container gestartet wird

``docker run --rm --gpus 2 nvidia/cuda nvidia-smi``

``docker run --rm --gpus all nvidia/cuda nvidia-smi ``

``docker run --gpus '"device=1,2"' nvidia/cuda nvidia-smi --query-gpu=uuid --format=csv``

- NVIDIA_VISIBLE_DEVICES

``docker run --rm --runtime=nvidia -e NVIDIA_VISIBLE_DEVICES=all nvidia/cuda nvidia-smi ``

- NVIDIA_DRIVER_CAPABILITIES

``docker run --rm --runtime=nvidia \
    -e NVIDIA_VISIBLE_DEVICES=2,3 \
    -e NVIDIA_DRIVER_CAPABILITIES=compute,utility \
    nvidia/cuda nvidia-sm``
   
 ``docker run --rm --gpus 'all,"capabilities=compute,utility"' \
    nvidia/cuda:11.0.3-base-ubuntu20.04 nvidia-smi``
### Hashcat
![image](https://user-images.githubusercontent.com/107040049/174433919-1ad2b8ff-9469-4768-b331-d6aba4c717b8.png)
### Dockerfiles
siehe samples
