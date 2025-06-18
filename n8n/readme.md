# n8n mini swarm
This docker compose starts two docker containers:
1. The main n8n server, which is available through port 5678
2. A postgres server to save your workflows

The postgres server can also be used for memory in the workflows themselves

Note that there is a `.env` file with default values for the postgres admin name and password and so it is recommended to change these values.

This setup will allow you to have a local n8n server with persistent memory of your workflows, 
and where you can connect to your favorite services like chatGPT, Claude, etc. using API keys.
