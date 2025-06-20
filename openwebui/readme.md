# Build a local openwebUI interface using local Ollama models

## Introduction
This docker compose deploys a swarm of dockers: The openwebUI docker, the ollama docker, a tika docker and a docling docker.
It is intended for people who want to experiment with AI models using a local GPU, avoiding privacy, network availability, and propriatery issues.

- OpenwebUI docker, creates an interface that allows chatting with AI models through port 8080.
- Ollama docker is the AI model server on port 11434. It can host multiple LLMs (see https://ollama.com/search for a list of models).
- Tika is a lightweight document parsing engine that handles many types of documents. Uses port 9998.
- Docling is a larger document parsing model by IBM that has much better support for complex documents, images, tables, etc., and uses port 5001. It is, of course, also much heavier and much slower that tika.

The instructions above are tailored for a setup with docker running in WSL (windows system linux), 
but the definition of a dedicated network with a bridge should allow this to work on any system (I hope).
You may want to change the volume paths if your docker isn't running on linux.

### Accessing services from openwebui
The fact that the ollama, tika, and docling containers are explicitly named means that *within the network* they have an address of 
http://ollama:11434, http://tika:9998, and http://docling:5001.
This means that these are the addresses to specify in the settings for openwebui.
However, to check that the services are up and running you still need to point your browser to localhost:11434, etc.

### Note 
Many of these dockers require downloading several Gs of layers or models. Do not use this over a limited or metered network.

## Pre-installation for using GPUs with docker
- Make sure that you have the latest drivers for you GPU
- Enable cuda-toolkit from within ubuntu by following [these instructions](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local).
- Within ubuntu, install the nvidia-container-toolkit by following [these instructions](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).
Now, the gpu resource should be available when starting a container.
