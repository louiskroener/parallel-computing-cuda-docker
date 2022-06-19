# GPU Virtualisierung (mit Docker)
## Installation (WSL 2 Ubuntu)
- WSL2 Ubuntu aufsetzen (siehe Microsoft Docs)
- Docker Desktop installieren und Docker für WSL2 Ubuntu aktivieren
- gcc installieren (falls noch nicht vorhanden)
- https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=runfile_local
- Cuda installieren mit präferierter Methode siehe Link
- check mit nvidia-smi (Cuda Treiber läuft local)
![image](https://user-images.githubusercontent.com/107040049/174431490-c068eaca-9666-4589-9aaf-bf54b31f6e02.png)
- sudo docker run --gpus all nvcr.io/nvidia/k8s/cuda-sample:nbody nbody -gpu -benchmark
![image](https://user-images.githubusercontent.com/107040049/174431593-f165dc29-406c-46bb-8bf8-5404edd711a6.png)
- check ob cuda über container läuft 
- docker run --rm --gpus all nvidia/cuda:11.7.0-runtime-ubuntu20.04 nvidia-smi ( auf Cuda Version achten (selbhe wie vom System) )
![image](https://user-images.githubusercontent.com/107040049/174431678-51bece42-ddf9-4efd-96c8-06c83837c9cc.png)
## Praktische Beispiele
- Dockerfile
- Varianten 
- Was lässt uns Cuda in / über Docker steueren 
![image](https://user-images.githubusercontent.com/107040049/174433919-1ad2b8ff-9469-4768-b331-d6aba4c717b8.png)
