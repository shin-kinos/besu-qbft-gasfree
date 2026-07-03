# Hyperledger Besu QBFT Private Network (Gas-Free)

A minimal **Hyperledger Besu (v25+)** private blockchain using **QBFT (Proof of Authority)** consensus with a **single validator**. This repository is intended for local development, testing, and demonstrations.

## Description

* QBFT (PoA) consensus
* Single validator
* Gas-free transactions (`zeroBaseFee=true`, `min-gas-price=0`)
* Chain ID **4649**
* 10-second block time
* London EVM enabled from genesis
* Pre-funded test accounts

## Running the Network

Ensure that Besu (v25+) is available on tour machine. Start the validator node with:

```bash
besu --config-file=config.toml
```

The node will:

* initialise the blockchain from `genesis.json`
* store data under `besu-data/`
* use the validator key in `key`
* expose JSON-RPC at:

```
http://127.0.0.1:4989
```

## Network Parameters

| Parameter           |               Value |
| ------------------- | ------------------: |
| Consensus           |                QBFT |
| Chain ID            |                4649 |
| Block Time          |          10 seconds |
| Epoch Length        |              30,000 |
| Request Timeout     |           4 seconds |
| Base Fee            |            Disabled |
| Minimum Gas Price   |                   0 |
| Contract Size Limit | 2,147,483,647 bytes |

## Verify the Network

Retrieve the latest block number:

```bash
curl -X POST http://127.0.0.1:4989 \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'
```

## ⚠️ Security Notice

The validator private key included in `key` is the same **public sample key** used in [the official Hyperledger Besu documentation and examples](https://docs.besu-eth.org/private-networks/tutorials/qbft). It is included only for convenience when running this demonstration network.

**Do not use this key, the pre-funded accounts, or this genesis configuration in any production or publicly accessible blockchain.**
