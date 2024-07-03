# Heat Server CENTOS setup

You can run a HEAT node on a 6 dollar a month digital ocean virtual machine, these are available here.

https://www.digitalocean.com/pricing/droplets#basic-droplets

When you create a droplet and choose CENTOS as its OS the below instructions will help you get started.

## Preparation

Prepare your fresh CENTOS server with a single command (installs docker, sets up a heatledger user)

```[bash]
sudo yum update -y; sudo yum install -y yum-utils device-mapper-persistent-data lvm2; sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo; sudo yum install -y docker-ce docker-ce-cli containerd.io; sudo systemctl start docker; sudo systemctl enable docker; sudo adduser heatledger; sudo usermod -aG docker heatledger; echo "Setup complete. Docker and user 'heatledger' are ready."
```

## Installation

Now create the starter script at `/home/heatledger/starter.sh`

```
sudo yum install nano -y
nano /home/heatledger/starter.sh
```

Copy the contents below to `/home/heatledger/starter.sh`

```
#!/bin/bash

# User Configuration: Set the location for the heatledger configuration folder.
# Uncomment the next line and replace '/path/to/heatledger' with your desired path.
#FOLDER_LOCATION="/path/to/heatledger"

# Choose which heat server version to run.
DOCKER_IMAGE=heatcrypto/heatledger:4.3.1

# Default to the script's directory appended with 'heatledger' if no custom path is provided.
: ${FOLDER_LOCATION:="$(dirname "$(readlink -f "$0")")/heatledger"}

echo "Starting HEAT server at $FOLDER_LOCATION"

# Ensure the configuration and blockchain directories exist
mkdir -p "${FOLDER_LOCATION}/conf"
mkdir -p "${FOLDER_LOCATION}/blockchain"

# Path to the properties file
PROPERTIES_FILE="${FOLDER_LOCATION}/conf/heat.properties"

# Write the heatledger configuration properties to the file using a heredoc
cat > "${PROPERTIES_FILE}" << EOF
heat.numberOfForkConfirmations=2
heat.enableAPIServer=true
heat.allowedBotHosts=*
heat.apiServerHost=0.0.0.0
heat.websocketServerHost=0.0.0.0
EOF

# Start the Docker container with the configuration directory mounted
# Add -d to run in  background
docker run -d \
  -p 7733:7733 \
  -p 7755:7755 \
  --restart=on-failure:1 \
  -v "${PROPERTIES_FILE}:/conf/heat.properties" \
  -v "${FOLDER_LOCATION}/blockchain:/blockchain" \
  $DOCKER_IMAGE
```

If you wish to add configurations you can do so in the heredoc section above (like setup your forger key).

## Run the server

Now run the `starter.sh` script to start your HEAT server.

```
bash /home/heatledger/starter.sh
```

Make sure you stop your docker container when making changes, the start it with the `starter.sh` script.
