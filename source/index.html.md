---
title: SolC API Documentation

toc_footers:
  - <a href='mailto:support@smartcontract.com'>Need Help?</a>

includes:
  - errors

search: true
---

# Overview

Welcome to the SolC API documentation. The SolC API is a minimal wrapper around the [Solidity Compiler](https://github.com/ethereum/solc-js), making it available via a simple web API. View the [source code here](https://github.com/oraclekit/solc-api).

The SolC API is part of the Smart Contarct Oracle Kit, but can stand alone as its own service. [Learn more about the Oracle Kit here](https://github.com/ethereum/solc-js).

There is a free version of the [SolC API available here](https://solc.smartcontract.com).

# API

## Compile

```shell
curl -X POST
  -d '{"Owned.sol": "pragma solidity ^0.4.6;...", "Oracle.sol": "pragma solidity ^0.4.9;..."}'
  https://solc.smartcontract.com/api/compile
```

`POST` request to `/api/compile` with parameters:

Parameter | Type | Description
---- | ----- | --------
* | string | Pass in a Solidity file to be compiled. To make it easy to follow feedback from the compiler, it is reccomended that you name each key the file name that you would call the code by if it were saved as a file.

You can send multiple files at once if your contracts import other contracts or libraries. To compile multiple files, simply include multiple keys, each being the file name.

Return values:

Parameter | Type | Description
---- | ----- | --------
contracts | object | A JSON object of all the information of the compiled contracts
formal | object | Errors and warnings raised by the (prototype) formal verification checks.
sourceList | array | List of files sent into the compiler.
sources | object | Abstract syntax trees for the compiled contracts.
