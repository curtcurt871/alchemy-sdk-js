[alchemy-sdk](../README.md) / [Exports](../modules.md) / CoreNamespace

# Class: CoreNamespace

The core namespace contains all commonly-used [Ethers.js
Provider](https://docs.ethers.io/v5/api/providers/api-providers/#AlchemyProvider)
methods. If you are already using Ethers.js, you should be simply able to
replace the Ethers.js Provider object with `alchemy.core` when accessing
provider methods and it should just work.

Do not call this constructor directly. Instead, instantiate an Alchemy object
with `const alchemy = new Alchemy(config)` and then access the core namespace
via `alchemy.core`.

## Table of contents

### Methods

- [call](CoreNamespace.md#call)
- [estimateGas](CoreNamespace.md#estimategas)
- [findContractDeployer](CoreNamespace.md#findcontractdeployer)
- [getAssetTransfers](CoreNamespace.md#getassettransfers)
- [getBalance](CoreNamespace.md#getbalance)
- [getBlock](CoreNamespace.md#getblock)
- [getBlockNumber](CoreNamespace.md#getblocknumber)
- [getBlockWithTransactions](CoreNamespace.md#getblockwithtransactions)
- [getCode](CoreNamespace.md#getcode)
- [getFeeData](CoreNamespace.md#getfeedata)
- [getGasPrice](CoreNamespace.md#getgasprice)
- [getLogs](CoreNamespace.md#getlogs)
- [getNetwork](CoreNamespace.md#getnetwork)
- [getStorageAt](CoreNamespace.md#getstorageat)
- [getTokenBalances](CoreNamespace.md#gettokenbalances)
- [getTokenMetadata](CoreNamespace.md#gettokenmetadata)
- [getTransaction](CoreNamespace.md#gettransaction)
- [getTransactionCount](CoreNamespace.md#gettransactioncount)
- [getTransactionReceipt](CoreNamespace.md#gettransactionreceipt)
- [getTransactionReceipts](CoreNamespace.md#gettransactionreceipts)
- [ready](CoreNamespace.md#ready)
- [send](CoreNamespace.md#send)
- [sendTransaction](CoreNamespace.md#sendtransaction)
- [waitForTransaction](CoreNamespace.md#waitfortransaction)

## Methods

### call

▸ **call**(`transaction`, `blockTag?`): `Promise`<`string`\>

Returns the result of executing the transaction, using call. A call does
not require any ether, but cannot change any state. This is useful for
calling getters on Contracts.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `transaction` | `Deferrable`<`TransactionRequest`\> | The transaction to execute. |
| `blockTag?` | `BlockTag` \| `Promise`<`BlockTag`\> | The optional block number or hash to get the call for. |

#### Returns

`Promise`<`string`\>

#### Defined in

[src/api/core-namespace.ts:216](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L216)

___

### estimateGas

▸ **estimateGas**(`transaction`): `Promise`<`BigNumber`\>

Returns an estimate of the amount of gas that would be required to submit
transaction to the network.

An estimate may not be accurate since there could be another transaction on
the network that was not accounted for, but after being mined affects the
relevant state.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `transaction` | `Deferrable`<`TransactionRequest`\> | The transaction to estimate gas for. |

#### Returns

`Promise`<`BigNumber`\>

#### Defined in

[src/api/core-namespace.ts:235](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L235)

___

### findContractDeployer

▸ **findContractDeployer**(`contractAddress`): `Promise`<[`DeployResult`](../interfaces/DeployResult.md)\>

Finds the address that deployed the provided contract and block number it
was deployed in.

NOTE: This method performs a binary search across all blocks since genesis
and can take a long time to complete. This method is a convenience method
that will eventually be replaced by a single call to an Alchemy endpoint
with this information cached.

**`beta`**

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `contractAddress` | `string` | The contract address to find the deployer for. |

#### Returns

`Promise`<[`DeployResult`](../interfaces/DeployResult.md)\>

#### Defined in

[src/api/core-namespace.ts:357](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L357)

___

### getAssetTransfers

▸ **getAssetTransfers**(`params`): `Promise`<[`AssetTransfersWithMetadataResponse`](../interfaces/AssetTransfersWithMetadataResponse.md)\>

Get transactions for specific addresses. See the web documentation for the
full details:
https://docs.alchemy.com/alchemy/enhanced-apis/transfers-api#alchemy_getassettransfers

This overload requires [AssetTransfersWithMetadataParams.withMetadata](../interfaces/AssetTransfersWithMetadataParams.md#withmetadata)
to be set to `true`, which results in additional metadata returned in the
response object.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `params` | [`AssetTransfersWithMetadataParams`](../interfaces/AssetTransfersWithMetadataParams.md) | An object containing fields for the asset transfer query |

#### Returns

`Promise`<[`AssetTransfersWithMetadataResponse`](../interfaces/AssetTransfersWithMetadataResponse.md)\>

#### Defined in

[src/api/core-namespace.ts:440](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L440)

▸ **getAssetTransfers**(`params`): `Promise`<[`AssetTransfersResponse`](../interfaces/AssetTransfersResponse.md)\>

Get transactions for specific addresses. See the web documentation for the
full details:
https://docs.alchemy.com/alchemy/enhanced-apis/transfers-api#alchemy_getassettransfers

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `params` | [`AssetTransfersParams`](../interfaces/AssetTransfersParams.md) | An object containing fields for the asset transfer query. |

#### Returns

`Promise`<[`AssetTransfersResponse`](../interfaces/AssetTransfersResponse.md)\>

#### Defined in

[src/api/core-namespace.ts:452](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L452)

___

### getBalance

▸ **getBalance**(`addressOrName`, `blockTag?`): `Promise`<`BigNumber`\>

Returns the balance of a given address as of the provided block.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `addressOrName` | `string` \| `Promise`<`string`\> | The address or name of the account to get the balance for. |
| `blockTag?` | `BlockTag` \| `Promise`<`BlockTag`\> | The optional block number or hash to get the balance for.   Defaults to 'latest' if unspecified. |

#### Returns

`Promise`<`BigNumber`\>

#### Defined in

[src/api/core-namespace.ts:55](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L55)

___

### getBlock

▸ **getBlock**(`blockHashOrBlockTag`): `Promise`<`Block`\>

Returns the block from the network based on the provided block number or
hash. Transactions on the block are represented as an array of transaction
hashes. To get the full transaction details on the block, use
[getBlockWithTransactions](CoreNamespace.md#getblockwithtransactions) instead.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `blockHashOrBlockTag` | `BlockTag` \| `Promise`<`BlockTag`\> | The block number or hash to get the block for. |

#### Returns

`Promise`<`Block`\>

#### Defined in

[src/api/core-namespace.ts:125](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L125)

___

### getBlockNumber

▸ **getBlockNumber**(): `Promise`<`number`\>

Returns the block number of the most recently mined block.

#### Returns

`Promise`<`number`\>

#### Defined in

[src/api/core-namespace.ts:162](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L162)

___

### getBlockWithTransactions

▸ **getBlockWithTransactions**(`blockHashOrBlockTag`): `Promise`<`BlockWithTransactions`\>

Returns the block from the network based on the provided block number or
hash. Transactions on the block are represented as an array of
{@link TransactionResponse} objects.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `blockHashOrBlockTag` | `BlockTag` \| `Promise`<`BlockTag`\> | The block number or hash to get the block for. |

#### Returns

`Promise`<`BlockWithTransactions`\>

#### Defined in

[src/api/core-namespace.ts:140](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L140)

___

### getCode

▸ **getCode**(`addressOrName`, `blockTag?`): `Promise`<`string`\>

Returns the contract code of the provided address at the block. If there is
no contract deployed, the result is `0x`.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `addressOrName` | `string` \| `Promise`<`string`\> | The address or name of the account to get the code for. |
| `blockTag?` | `BlockTag` \| `Promise`<`BlockTag`\> | The optional block number or hash to get the code for.   Defaults to 'latest' if unspecified. |

#### Returns

`Promise`<`string`\>

#### Defined in

[src/api/core-namespace.ts:72](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L72)

___

### getFeeData

▸ **getFeeData**(): `Promise`<`FeeData`\>

Returns the recommended fee data to use in a transaction.

For an EIP-1559 transaction, the maxFeePerGas and maxPriorityFeePerGas
should be used.

For legacy transactions and networks which do not support EIP-1559, the
gasPrice should be used.

#### Returns

`Promise`<`FeeData`\>

#### Defined in

[src/api/core-namespace.ts:188](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L188)

___

### getGasPrice

▸ **getGasPrice**(): `Promise`<`BigNumber`\>

Returns the best guess of the current gas price to use in a transaction.

#### Returns

`Promise`<`BigNumber`\>

#### Defined in

[src/api/core-namespace.ts:172](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L172)

___

### getLogs

▸ **getLogs**(`filter`): `Promise`<`Log`[]\>

Returns an array of logs that match the provided filter.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `filter` | `Filter` \| `FilterByBlockHash` \| `Promise`<`Filter` \| `FilterByBlockHash`\> | The filter object to use. |

#### Returns

`Promise`<`Log`[]\>

#### Defined in

[src/api/core-namespace.ts:326](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L326)

___

### getNetwork

▸ **getNetwork**(): `Promise`<`Network`\>

Returns the {@link EthersNetworkAlias} Alchemy is connected to.

#### Returns

`Promise`<`Network`\>

#### Defined in

[src/api/core-namespace.ts:152](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L152)

___

### getStorageAt

▸ **getStorageAt**(`addressOrName`, `position`, `blockTag?`): `Promise`<`string`\>

Return the value of the provided position at the provided address, at the
provided block in `Bytes32` format.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `addressOrName` | `string` \| `Promise`<`string`\> | The address or name of the account to get the code for. |
| `position` | `BigNumberish` \| `Promise`<`BigNumberish`\> | The position of the storage slot to get. |
| `blockTag?` | `BlockTag` \| `Promise`<`BlockTag`\> | The optional block number or hash to get the code for.   Defaults to 'latest' if unspecified. |

#### Returns

`Promise`<`string`\>

#### Defined in

[src/api/core-namespace.ts:90](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L90)

___

### getTokenBalances

▸ **getTokenBalances**(`address`, `contractAddresses?`): `Promise`<[`TokenBalancesResponse`](../interfaces/TokenBalancesResponse.md)\>

Returns the token balances for a specific owner address given a list of contracts.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `address` | `string` | The owner address to get the token balances for. |
| `contractAddresses?` | `string`[] | A list of contract addresses to check. If omitted,   the top 100 tokens by 24 hour volume will be checked. |

#### Returns

`Promise`<[`TokenBalancesResponse`](../interfaces/TokenBalancesResponse.md)\>

#### Defined in

[src/api/core-namespace.ts:396](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L396)

___

### getTokenMetadata

▸ **getTokenMetadata**(`address`): `Promise`<[`TokenMetadataResponse`](../interfaces/TokenMetadataResponse.md)\>

Returns metadata for a given token contract address.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `address` | `string` | The contract address to get metadata for. |

#### Returns

`Promise`<[`TokenMetadataResponse`](../interfaces/TokenMetadataResponse.md)\>

#### Defined in

[src/api/core-namespace.ts:419](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L419)

___

### getTransaction

▸ **getTransaction**(`transactionHash`): `Promise`<``null`` \| `TransactionResponse`\>

Returns the transaction with hash or null if the transaction is unknown.

If a transaction has not been mined, this method will search the
transaction pool. Various backends may have more restrictive transaction
pool access (e.g. if the gas price is too low or the transaction was only
recently sent and not yet indexed) in which case this method may also return null.

NOTE: This is an alias for [TransactNamespace.getTransaction](TransactNamespace.md#gettransaction).

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `transactionHash` | `string` \| `Promise`<`string`\> | The hash of the transaction to get. |

#### Returns

`Promise`<``null`` \| `TransactionResponse`\>

#### Defined in

[src/api/core-namespace.ts:255](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L255)

___

### getTransactionCount

▸ **getTransactionCount**(`addressOrName`, `blockTag?`): `Promise`<`number`\>

Returns the number of transactions ever sent from the provided address, as
of the provided block tag. This value is used as the nonce for the next
transaction from the address sent to the network.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `addressOrName` | `string` \| `Promise`<`string`\> | The address or name of the account to get the nonce for. |
| `blockTag?` | `BlockTag` \| `Promise`<`BlockTag`\> | The optional block number or hash to get the nonce for. |

#### Returns

`Promise`<`number`\>

#### Defined in

[src/api/core-namespace.ts:108](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L108)

___

### getTransactionReceipt

▸ **getTransactionReceipt**(`transactionHash`): `Promise`<``null`` \| `TransactionReceipt`\>

Returns the transaction receipt for hash or null if the transaction has not
been mined.

To stall until the transaction has been mined, consider the
waitForTransaction method below.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `transactionHash` | `string` \| `Promise`<`string`\> | The hash of the transaction to get. |

#### Returns

`Promise`<``null`` \| `TransactionReceipt`\>

#### Defined in

[src/api/core-namespace.ts:272](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L272)

___

### getTransactionReceipts

▸ **getTransactionReceipts**(`params`): `Promise`<[`TransactionReceiptsResponse`](../interfaces/TransactionReceiptsResponse.md)\>

Gets all transaction receipts for a given block by number or block hash.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `params` | [`TransactionReceiptsParams`](../modules.md#transactionreceiptsparams) | An object containing fields for the transaction receipt query. |

#### Returns

`Promise`<[`TransactionReceiptsResponse`](../interfaces/TransactionReceiptsResponse.md)\>

#### Defined in

[src/api/core-namespace.ts:483](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L483)

___

### ready

▸ **ready**(): `Promise`<`Network`\>

Returns a Promise which will stall until the network has heen established,
ignoring errors due to the target node not being active yet.

This can be used for testing or attaching scripts to wait until the node is
up and running smoothly.

#### Returns

`Promise`<`Network`\>

#### Defined in

[src/api/core-namespace.ts:202](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L202)

___

### send

▸ **send**(`method`, `params`): `Promise`<`any`\>

Allows sending a raw message to the Alchemy backend.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `method` | `string` | The method to call. |
| `params` | `any`[] | The parameters to pass to the method. |

#### Returns

`Promise`<`any`\>

#### Defined in

[src/api/core-namespace.ts:340](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L340)

___

### sendTransaction

▸ **sendTransaction**(`signedTransaction`): `Promise`<`TransactionResponse`\>

Submits transaction to the network to be mined. The transaction must be
signed, and be valid (i.e. the nonce is correct and the account has
sufficient balance to pay for the transaction).

NOTE: This is an alias for [TransactNamespace.getTransaction](TransactNamespace.md#gettransaction).

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `signedTransaction` | `string` \| `Promise`<`string`\> | The signed transaction to send. |

#### Returns

`Promise`<`TransactionResponse`\>

#### Defined in

[src/api/core-namespace.ts:289](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L289)

___

### waitForTransaction

▸ **waitForTransaction**(`transactionHash`, `confirmations?`, `timeout?`): `Promise`<``null`` \| `TransactionReceipt`\>

Returns a promise which will not resolve until specified transaction hash is mined.

If {@link confirmations} is 0, this method is non-blocking and if the
transaction has not been mined returns null. Otherwise, this method will
block until the transaction has confirmed blocks mined on top of the block
in which it was mined.

NOTE: This is an alias for [TransactNamespace.getTransaction](TransactNamespace.md#gettransaction).

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `transactionHash` | `string` | The hash of the transaction to wait for. |
| `confirmations?` | `number` | The number of blocks to wait for. |
| `timeout?` | `number` | The maximum time to wait for the transaction to confirm. |

#### Returns

`Promise`<``null`` \| `TransactionReceipt`\>

#### Defined in

[src/api/core-namespace.ts:311](https://github.com/alchemyplatform/alchemy-sdk-js/blob/145ea50/src/api/core-namespace.ts#L311)
