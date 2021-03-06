# Get Started

## Install Solidity 0.6.0 (Optional)

### Ubuntu 18.04:

```
sudo apt install software-properties-common
sudo add-apt-repository ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install solc
```

### Mac OS X:

```
brew update
brew upgrade
brew tap ethereum/ethereum
brew install solidity
```

## Setup Python Environment

```
python3.7 -m pip install virtualenv
python3.7 -m virtualenv .venv
. .venv/bin/activate
```

### Install PyEosKit

#### Ubuntu

```
python3.7 -m pip install https://github.com/learnforpractice/pyeoskit/releases/download/v0.7.0/pyeoskit-0.7.0-cp37-cp37m-linux_x86_64.whl
```

#### Mac OS X
```
python3.7 -m pip install https://github.com/learnforpractice/pyeoskit/releases/download/v0.7.0/pyeoskit-0.7.0-cp37-cp37m-macosx_10_9_x86_64.whl
```

### Install Jupyter Notebook
```
python3.7 -m pip install notebook
```

### Install Solc Compiler
```
python3.7 -m pip install py-solc-x
```

### Install Web3

```
python3.7 -m pip install --pre web3[tester]==5.5.0
```

### Install Base58
```
python3.7 -m pip install base58
```

## Start a Testnet
```
rm -r dd
nodeos  --verbose-http-errors  --http-max-response-time-ms 100 --data-dir dd --config-dir cd --wasm-runtime eos-vm-jit --contracts-console -p eosio -e --plugin eosio::producer_plugin --plugin eosio::chain_api_plugin --plugin eosio::producer_api_plugin
```

In order to pass `test_ecrecover` and `test_sign_with_eth_private_key` testcase in evm_test.py, start nodeos with `--eos-vm-oc-enable` option as show below:

```
rm -r dd
nodeos --eos-vm-oc-enable --verbose-http-errors  --http-max-response-time-ms 100 --data-dir dd --config-dir cd --wasm-runtime eos-vm-jit --contracts-console -p eosio -e --plugin eosio::producer_plugin --plugin eosio::chain_api_plugin --plugin eosio::producer_api_plugin
```

## Initialize the Testnet
In the same directory, run the following command:
```
python3.7 testnet-init.py http://127.0.0.1:8888
```

modify http://127.0.0.1:8888 to the right url if nodeos's http server is not listening at the default ip and port


## Run TestCase

In the same directory, run the following command:

```
python3.7 evm_test.py http://127.0.0.1:8888
```

modify http://127.0.0.1:8888 to the right url if nodeos's http server is not listening at the default ip and port

## Run VMTests

```
python3.7 testsrunner.py -- --http-server-address http://127.0.0.1:8888 -d VMTests -v 0
```

Notes:

```
There are 609 evm tests in VMTests directory, 123 vm tests will throw exceptions from evm as expected, other tests will not throw exceptions as pass the result checking.

Refer to test script in testsrunner.py for how it works.

```

## Interact With EVM4EOSIO Via Ethereum RPC Interface

Python script eth2eosbridge.py enables applications to interact with EVM smart contract on EOSIO through the Ethereum RPC Interface, so that Dapp on Ethereum can be easily ported to the EOSIO platform.

To use this tool run the following command to install required Python packages.

```
python3.7 -m pip install plyvel
python3.7 -m pip install flask
python3.7 -m pip install flask_cors
```

Run the following command to start this tool

```
python3.7 eth2eosbridge.py
```

## Demo Video

[Demo](https://www.youtube.com/watch?v=K2-laWNcsVM&feature=youtu.be)

