Network Stats Dashboard
============

This is the backend service which runs along with node and tracks the network status, fetches information through WS-RPC and connects through WebSockets to feed information.

# How to add your node

## Prerequisite
* parity or geth
* node
* npm

## Configuration

Configure the app modifying [processes.json](/processes.json). Note that you have to modify the backup processes.json file located in `./processes.json` (to allow you to set your env vars without being rewritten when updating).

```bash
[
  {
    "name"              : "Ethereum Classic",
    "script"            : "app.js",
    "log_date_format"   : "YYYY-MM-DD HH:mm Z",
    "merge_logs"        : false,
    "watch"             : false,
    "max_restarts"      : 10,
    "exec_interpreter"  : "node",
    "exec_mode"         : "fork_mode",
    "env":
    {
      "NODE_ENV"        : "Ethereum Classic",
      "RPC_HOST"        : "localhost",
      "RPC_PORT"        : "8545",
      "LISTENING_PORT"  : "30303",
      "INSTANCE_NAME"   : "ua-mining.com Ethereum Classic PPLNS",
      "CONTACT_DETAILS" : "etc.ua-mining.com",
      "WS_SERVER"       : "wss://etc-stats.ua-mining.com",
      "WS_SECRET"       : "asdf",
      "VERBOSITY"       : 0
    }
  }
]
```

## GET and Run

Get it using git:

```bash
cd ~
git clone https://github.com/ua-mining/netstats-cli
cd ~/netstats-cli
npm install
```
sudo npm install pm2@latest -g

Run it using pm2:

```bash
cd ~/netstats-cli
pm2 start processes.json
pm2 startup
```
