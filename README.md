# Rasabot-quickstart
This is simple chat Bot using Rasa Stack. 

## Pre-requisites:
For windows:

### Install Python:

  - Download Windows x86-64 executable installer from link below and install:
  - https://www.python.org/downloads/release/python-367/
### Install VC++ Build tools:

- Download the Visual C++ buildtools executable from link below and install:
- https://visualstudio.microsoft.com/visual-cpp-build-tools/

### Update pip:
- python -m pip install --upgrade pip`

### Install rasa-core & rasa-nlu:
- pip install rasa_core==0.11
- pip install rasa_nlu[spacy]==0.13.8
- python -m spacy download en_core_web_md
- python -m spacy link en_core_web_md en

# Steps to start Chat Bot

  @echo "    train-nlu"
	@echo "        Trains a new nlu model using the projects Rasa NLU config"
	@echo "    train-core"
	@echo "        Trains a new dialogue model using the story training data"
	@echo "    action-server"
	@echo "        Starts the server for custom action."
	@echo "    cmdline"
	@echo "       This will load the assistant in your terminal for you to chat."
  
 #### train-nlu:
	python -m rasa_nlu.train -c nlu_config.yml --data data/nlu_data.md -o models --fixed_model_name nlu --project current --verbose

#### train-core:
	python -m rasa_core.train -d domain.yml -s data/stories.md -o models/current/dialogue -c policies.yml

#### cmdline:
	python -m rasa_core.run -d models/current/dialogue -u models/current/nlu --endpoints endpoints.yml
	
#### action-server:
	python -m rasa_core_sdk.endpoint --actions actions
  
### To Start bot:
    -  action-server
    -  cmdline
