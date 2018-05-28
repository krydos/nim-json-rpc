**Nim-eth-rpc**

[![Build Status (Travis)](https://img.shields.io/travis/status-im/nim-eth-rpc/master.svg?label=Linux%20/%20macOS "Linux/macOS build status (Travis)")](https://travis-ci.org/status-im/nim-eth-rpc)
[![Windows build status (Appveyor)](https://img.shields.io/appveyor/ci/jarradh/nim-eth-rpc/master.svg?label=Windows "Windows build status (Appveyor)")](https://ci.appveyor.com/project/jarradh/nim-eth-rpc)

Nim-eth-rpc is designed to provide remote procedure calls to the Nimbus Ethereum research project.

# Installation

`git clone https://github.com/status-im/nim-eth-rpc`


## Requirements
* Nim 17.3 and up


# Usage

## Server

```nim
import rpcserver, asyncdispatch

when isMainModule:
  var srv = newRpcServer("")
  asyncCheck srv.serve()
  runForever()
```

## Client

```nim
import rpcclient, asyncdispatch, json

proc main {.async.} =
  var client = newRpcClient()
  await client.connect("localhost", Port(8545))
  let response = waitFor client.web3_clientVersion(newJNull())
  echo response.result.pretty

waitFor main()

```

# Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

# License
[MIT](https://choosealicense.com/licenses/mit/)
