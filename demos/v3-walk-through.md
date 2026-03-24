# SCADABLE V3 Demo Guide

## 1. Log In

Go to [dashboard.scadable.com](https://dashboard.scadable.com) and log in. You can use Google OAuth or a password provided by the Scadable team.

## 2. Add Your SSH Key

Go to **Settings** > **Security** and add your public SSH key. If you don't have one:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
```

Copy the output and paste it into the dashboard. Click **Save**.

## 3. Create a Namespace

A namespace is the top-level container for all your IoT deployments. Click **Create Namespace** and give it a name.

## 4. Create a Project

Inside your namespace, go to the **Projects** tab and create a new project. A project holds the device configurations that get deployed to your gateways.

## 5. Deploy Your First Gateway

Go to **Gateways**, click **Add**, pick a name, and select the project you just created. You will get an install command. Copy it and run it on your device:

```bash
curl -sL https://get.scadable.com/install | sh -s -- --code YOUR_REGISTRATION_CODE
```

Click **OK**. If the device comes online in the dashboard, you are done.

## 6. Dispatch the AI Agent

Open the gateway detail page. Go to the **Maintenance** tab and click the **+** button. Paste this objective:

```
Install Docker on this gateway using apt-get. Then pull and run the Modbus TCP simulator container: docker run -d --name modbus-sim -p 5020:5020 oitc/modbus-server. Verify it is running and responding on port 5020.
```

Set agent type to **health-agent** and click **Dispatch**. Watch the agent work in real time. It will install Docker, pull the container, and start it.

## 7. SSH Into the Gateway

First, go to the **Members** tab in your namespace and make sure SSH is enabled on your name.

Then SSH in from your terminal:

```bash
ssh YOUR_GATEWAY_ID@ssh.scadable.com
```

Verify Docker was installed and the simulator is running:

```bash
docker -v
docker ps
```

You should see the `modbus-sim` container running on port 5020. Type `exit` to disconnect.

## 8. Clone the Project Repository

Go to the **Projects** tab, open your project, and copy the SSH clone URL. Then on your machine:

```bash
git clone git@git.scadable.com:YOUR_NAMESPACE/YOUR_PROJECT.git
cd YOUR_PROJECT
```

## 9. Install the Edge Kit

```bash
pip install scadable-cli
```

## 10. Add a Device

The project has already been initialized by the Scadable engine. Just add a new Modbus TCP device:

```bash
scadable add device modbus-tcp modbus-sim
```

## 11. Configure the Device

Open the generated config file:

```bash
nano devices/modbus-sim/config.py
```

Set the connection details to point to the local simulator:

```python
from scadable.edge import Device, ModbusConnection
from scadable.edge.constants import MODBUS_TCP, FIVE_SEC
from dataclasses import dataclass

@dataclass
class Connection(ModbusConnection):
    host: str = "127.0.0.1"
    port: int = 5020
    slave_id: int = 1

class ModbusSim(Device):
    id = "modbus-sim"
    protocol = MODBUS_TCP
    connection = Connection
    frequency = FIVE_SEC
    filter = []
```

Save, then commit and push:

```bash
git add .
git commit -m "Add modbus-sim device"
git push
```

## 12. Make a Release

Go back to the dashboard, open your project, and go to the **Releases** tab. Create a new release. After it builds and deploys, your gateway will reload and start polling the Modbus simulator.

Verify data is flowing by checking the **Overview** tab on the gateway. You should see the device listed there.

## 13. Create an API Key

Go to your namespace **Settings** > **API Keys** and create a new key. Copy it immediately, it starts with `sk_live_`.

## 14. Use the Python SDK

```bash
pip install scadable
```

```python
from scadable import Scadable


client = Scadable(api_key="sk_live_YOUR_KEY_HERE")

for gw in client.gateways.list():
    print(f"{gw.name}: {gw.status}")

devices = client.gateways.devices("YOUR_GATEWAY_ID")
for d in devices:
    print(f"  {d.name} [{d.status}]")
```

You now have live Modbus data streaming through the Scadable platform into your Python application.
