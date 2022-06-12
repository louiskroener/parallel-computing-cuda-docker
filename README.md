# GPU Virtualisierung (mit Docker)
## Installation (WSL 2 Ubuntu)
- WSL2 Ubuntu aufsetzen (siehe Microsoft Docs)
- Docker Desktop installieren und Docker für WSL2 Ubuntu aktivieren
- gcc installieren (falls noch nicht vorhanden)
- https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=runfile_local
- Cuda installieren mit präferierter Methode siehe Link
- check mit nvidia-smi (Cuda Treiber läuft local)
- sudo docker run --gpus all nvcr.io/nvidia/k8s/cuda-sample:nbody nbody -gpu -benchmark
- check ob cuda über container läuft 
- docker run --rm --gpus all nvidia/cuda:11.7.0-runtime-ubuntu20.04 nvidia-smi ( auf Cuda Version achten (selbhe wie vom System) )
## Praktische Beispiele
- Dockerfile
- Varianten 
- Was lässt uns Cuda in / über Docker steueren 
### weitere Gedanken

- Abriss der Grundlagen der Virtualisierung ( insbensondere bezogen auf GPU / Cuda )
- Kubernetes 
- Vorteile / Nachteile der Virtualisierung
- auf weitere Technologien schauen wie podman, lxc
- containerd
- Vorraustezungen ( Docker Desktop etc, Linux, ... )
- 
