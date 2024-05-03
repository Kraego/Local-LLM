# About 

GIT Repo with Demo Install, following: https://docs.privategpt.dev/installation/getting-started/installation.
Try to create a docker stack. First on my local `arch` installation.

## Guide

### Install Ollama

* Install ollama
```shell
sudo systemctl start docker # optional
docker login # optional
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```
* check if it's running: http://localhost:11434 
* Get LLM Model/Embeddings:
```shell
docker exec -it [DOCKER_CONTAINER_ID] sh
ollama pull mistral
ollama pull nomic-embed-text
ollama serve
```

### Install privateGPT

**Install requirements:**
* installed pyenv: `sudo pacman -Sy pyenv`
* `cd private-gpt`
* cloned private-gpt: `git clone https://github.com/zylon-ai/private-gpt`
* install poetry: `sudo pacman -Sy poetry`

**Install privateGPT:**
* in a second terminal
```shell
pyenv local 3.11
pip install poetry # installed poetry (python backend)
poetry install --extras "ui llms-ollama embeddings-ollama vector-stores-qdrant"
```

**Run the whole thing:**

* `PGPT_PROFILES=ollama make run`
* Connect to privateGPT webUI: http://localhost:8001 

## As docker stack
