
# Docker Compose for Threshold Access Control #
Docker compose file for [Threshold Access Control (TACo)](https://github.com/nucypher/nucypher) to leverage the ease and convenience of docker compose. For detailed setup instructions for TACo see [official Threshold docs](https://docs.threshold.network/staking-and-running-a-node/taco-node-setup/run-a-taco-node-with-docker).

## Usage ##

### 1. Transfer compose file to your server ### 
Transfer the file to your server or create a new file named `compose.yaml` and paste the contents into it.

### 2. Make adjustments ###

Adjust paths for volume bindings and path for `nucypher.env`.

```bash
- /home/taco/.local/share/nucypher:/root/.local/share/nucypher:rw
- /home/taco/.cache/nucypher:/root/.cache/nucypher:rw
- /home/taco/.ethereum/:/root/.ethereum:ro


env_file:
- /home/taco/.local/share/nucypher/nucypher.env
```

### 3. Starting the node ###
Start the node omitting the detach flag to ensure everything is working as intended.

This may require `sudo` depending on your user.

```bash
docker compose up
```
Expected output:
```
[+] Running 2/2
 ✔ Network bin_default  Created
 ✔ Container ursula     Created
Attaching to ursula
 ✔ Container ursula     Created
Attaching to ursula
ursula  | Defaulting to Ursula configuration file: '/root/.local/share/nucypher/ursula.json'
ursula  | Authenticating Ursula
ursula  | State starting from scratch
ursula  | Loaded Ursula (mainnet)
ursula  | ✓ External IP matches configuration
ursula  | Starting services...
ursula  | ✓ P2P Networking (mainnet)
ursula  | ✓ DKG Ritual Tracking
ursula  | ✓ Operator 0xYOUR-OPERATOR-ADDRESS is funded with XX.XX MATIC
ursula  | ✓ Operator 0xYOUR-OPERATOR-ADDRESS is bonded to staking provider 0xYOUR-STAKING-PROVIDER-ADDRESS
ursula  | ! Checking provider's DKG participation public key for 0xYOUR-STAKING-PROVIDER-ADDRESS on Polygon/Mainnet at Coordinator 0xE74259e3dafe30bAA8700238e324b47aC98FE755
ursula  | ✓ Provider's DKG participation public key already set for 0xYOUR-STAKING-PROVIDER-ADDRESS on Coordinator 0xE74259e3dafe30bAA8700238e324b47aC98FE755
ursula  | ✓ Start Operator Bonded Tracker
ursula  | ✓ Rest Server https://11.11.11.11:9151
ursula  | Working ~ Keep Ursula Online!
```

press `CTRL` + `C` to exit.

Restart with the following:

```bash
sudo docker compose up -d
```

Expected output:

```
[+] Running 1/1
 ✔ Container ursula  Started
 ```
 
### Stopping the node ###

To stop
```bash
sudo docker compose down
```
Expected output:
```
[+] Running 0/1
 ⠏ Container ursula  Stopping
 
 [+] Running 2/2
 ✔ Container ursula     Removed
 ✔ Network bin_default  Removed
```

