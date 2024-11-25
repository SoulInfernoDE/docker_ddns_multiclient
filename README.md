# ddns_multiclient [![Docker Build Cloud](https://github.com/SoulInfernoDE/docker_ddns_multiclient/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/SoulInfernoDE/docker_ddns_multiclient/actions/workflows/build.yml)
Use [DomainConnectDDNS-Python](https://github.com/Domain-Connect/DomainConnectDDNS-Python) in a docker container, which executes the update command every 15 minutes. I do not know which providers are supported by this tool. I use it for [IONOS](https://www.ionos.com).

## Usage
### Download the image within the synology docker gui
    Go to the "Registry" and search for:
![grafik](https://github.com/user-attachments/assets/bdde5afe-9bbe-49eb-a9f1-02bd5e22b724)
    "Download" the image


### Run container (IMPORTANT! RUN THE CONTAINER IN NETWORK=HOST ESP. IF YOU ARE USING IPv6)
    - Go to the synology Image tab, select "ddns_multiclient" and press "Run":
    
![grafik](https://github.com/user-attachments/assets/6e00355e-af8a-4b89-a984-1e58ad00ad90)
    
    - Press "Next":
    
![grafik](https://github.com/user-attachments/assets/7d52ec23-6c24-4cbe-9d28-fdd5cc9c31ed)
    
    - Make a folder on your synology nas and create a file called "settings.txt"
![grafik](https://github.com/user-attachments/assets/0cf67760-7e2a-4fc2-9248-f851647cb3ce)

    - Switch back to the creation of the docker container and select the file settings.txt and link it to /usr/src/app/settings.txt:
![grafik](https://github.com/user-attachments/assets/e90cad56-4446-43fc-8595-8adbc14466d1)

    - Press "Next" and "finish". The Container should run and after you made your initial setup the settings.txt file contains
      your settings for restoring the ddns_multiclient when recreated




### Setup domains (Description for synology is WIP and will be done when i have spare time)
    - 
    docker exec -it domain-connect-ddns domain-connect-dyndns setup --domain <YOUR_DOMAIN>
Do this for each domain you want to set up.

### First update
    docker exec -it domain-connect-ddns domain-connect-dyndns update --all
Test the settings by starting the update manually once
