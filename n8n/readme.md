# n8n mini swarm
This docker compose starts two docker containers:
1. The main n8n server, which is available through port 5678
2. A postgres server to save your workflows

n8n is an interface that allows building automated workflows and AI agents with minimal or no code. 
The setup provided here will allow you to have a local n8n server with persistent memory of your workflows, 
and where you can connect to your favorite services like chatGPT, Claude, etc. using API keys.
The postgres server can also be used for memory in the workflows themselves

### Note 
There is a `.env` file with default values for the postgres admin name and password and it is therefore recommended to change these values.

