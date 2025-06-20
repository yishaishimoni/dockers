# Introduction
This setup creates an n8n service that can connect to local AI models served by an ollama service. 
It is basically a join of the n8n and openwebui docker-compose files.
Unlike the 8n8 setup, it allows using local AI models and so doesn't require any API keys, and so it's completely free.
On the other hand, local models usually have less reasoning and reflection capabilities and you may have to inject those into the workflow ourself.
Still, this is a great environment if you want to build local agents. 

### Notes
- The instructions here are tailored for a setup with docker running in WSL (windows system linux), 
but the definition of a dedicated network with a bridge should allow this to work on any system (I hope).
You may want to change the volume paths if your docker isn't running on linux.
- Many of these dockers require downloading several Gs of layers or models. Do not use this over a limited or metered network.
- Instructions to make sure that the dockers use a local GPU can be found in the [openwebui swarm readme](openwebui/readme.md#pre-installation-for-using-gpus-with-docker)
- The same readme also includes explanation how the services can access each other.
- There is a .env file with default values for the postgres admin name and password and it is therefore recommended to change these values.

# Containers in the swarm
The swarm contains the following containers:
1. The main n8n server, which is available through port 5678
2. A postgres server to save your workflows
3. OpenwebUI docker, creates an interface that allows chatting with AI models through port 8080.
4. Ollama docker is the AI model server on port 11434. It can host multiple LLMs (see https://ollama.com/search for a list of models).
5. Tika is a lightweight document parsing engine that handles many types of documents. Uses port 9998.
6. Docling is a larger document parsing model by IBM that has much better support for complex documents, images, tables, etc., and uses port 5001. It is, of course, also much heavier and much slower that tika.

 
