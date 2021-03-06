# Protocol Documentation
<a name="top"></a>

This reference is auto-generated from [aergoio/aergo-protobuf](https://github.com/aergoio/aergo-protobuf).


- [rpc.proto](#rpc.proto)
    - [AergoRPCService](#types.AergoRPCService)
  
    - [AccountAndRoot](#types.AccountAndRoot)
    - [BlockHeaderList](#types.BlockHeaderList)
    - [BlockMetadata](#types.BlockMetadata)
    - [BlockMetadataList](#types.BlockMetadataList)
    - [BlockchainStatus](#types.BlockchainStatus)
    - [CommitResult](#types.CommitResult)
    - [CommitResultList](#types.CommitResultList)
    - [Empty](#types.Empty)
    - [ImportFormat](#types.ImportFormat)
    - [Input](#types.Input)
    - [ListParams](#types.ListParams)
    - [Name](#types.Name)
    - [NameInfo](#types.NameInfo)
    - [NodeReq](#types.NodeReq)
    - [Output](#types.Output)
    - [Peer](#types.Peer)
    - [PeerList](#types.PeerList)
    - [Personal](#types.Personal)
    - [SingleBytes](#types.SingleBytes)
    - [Staking](#types.Staking)
    - [VerifyResult](#types.VerifyResult)
    - [Vote](#types.Vote)
    - [VoteList](#types.VoteList)
  
    - [CommitStatus](#types.CommitStatus)
    - [VerifyStatus](#types.VerifyStatus)
  
  

- [blockchain.proto](#blockchain.proto)
  
    - [ABI](#types.ABI)
    - [Block](#types.Block)
    - [BlockBody](#types.BlockBody)
    - [BlockHeader](#types.BlockHeader)
    - [ContractVarProof](#types.ContractVarProof)
    - [FnArgument](#types.FnArgument)
    - [Function](#types.Function)
    - [Query](#types.Query)
    - [Receipt](#types.Receipt)
    - [State](#types.State)
    - [StateProof](#types.StateProof)
    - [StateQuery](#types.StateQuery)
    - [StateQueryProof](#types.StateQueryProof)
    - [StateVar](#types.StateVar)
    - [Tx](#types.Tx)
    - [TxBody](#types.TxBody)
    - [TxIdx](#types.TxIdx)
    - [TxInBlock](#types.TxInBlock)
    - [TxList](#types.TxList)
  
    - [TxType](#types.TxType)
  
  

- [metric.proto](#metric.proto)
  
    - [Metrics](#types.Metrics)
    - [MetricsRequest](#types.MetricsRequest)
    - [PeerMetric](#types.PeerMetric)
  
    - [MetricType](#types.MetricType)
  
  

- [Scalar Value Types](#scalar-value-types)



<a name="rpc.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## rpc.proto



<a name="types.AergoRPCService"></a>

### AergoRPCService
AergoRPCService is the main RPC service providing endpoints to interact 
with the node and blockchain. If not otherwise noted, methods are unary requests.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| NodeState | [NodeReq](#types.NodeReq) | [SingleBytes](#types.SingleBytes) | Returns the current state of this node |
| Metric | [MetricsRequest](#types.MetricsRequest) | [Metrics](#types.Metrics) | Returns node metrics according to request |
| Blockchain | [Empty](#types.Empty) | [BlockchainStatus](#types.BlockchainStatus) | Returns current blockchain status (best block's height and hash) |
| ListBlockHeaders | [ListParams](#types.ListParams) | [BlockHeaderList](#types.BlockHeaderList) | Returns list of Blocks without body according to request |
| ListBlockMetadata | [ListParams](#types.ListParams) | [BlockMetadataList](#types.BlockMetadataList) | Returns list of block metadata (hash, header, and number of transactions) according to request |
| ListBlockStream | [Empty](#types.Empty) | [Block](#types.Block) | Returns a stream of new blocks as they get added to the blockchain |
| ListBlockMetadataStream | [Empty](#types.Empty) | [BlockMetadata](#types.BlockMetadata) | Returns a stream of new block's metadata as they get added to the blockchain |
| GetBlock | [SingleBytes](#types.SingleBytes) | [Block](#types.Block) | Return a single block, queried by hash or number |
| GetTX | [SingleBytes](#types.SingleBytes) | [Tx](#types.Tx) | Return a single transaction, queried by transaction hash |
| GetBlockTX | [SingleBytes](#types.SingleBytes) | [TxInBlock](#types.TxInBlock) | Return information about transaction in block, queried by transaction hash |
| GetReceipt | [SingleBytes](#types.SingleBytes) | [Receipt](#types.Receipt) | Return transaction receipt, queried by transaction hash |
| GetABI | [SingleBytes](#types.SingleBytes) | [ABI](#types.ABI) | Return ABI stored at contract address |
| SendTX | [Tx](#types.Tx) | [CommitResult](#types.CommitResult) | Sign and send a transaction from an unlocked account |
| SignTX | [Tx](#types.Tx) | [Tx](#types.Tx) | Sign transaction with unlocked account |
| VerifyTX | [Tx](#types.Tx) | [VerifyResult](#types.VerifyResult) | Verify validity of transaction |
| CommitTX | [TxList](#types.TxList) | [CommitResultList](#types.CommitResultList) | Commit a signed transaction |
| GetState | [SingleBytes](#types.SingleBytes) | [State](#types.State) | Return state of account |
| GetStateAndProof | [AccountAndRoot](#types.AccountAndRoot) | [StateProof](#types.StateProof) | Return state of account, including merkle proof |
| CreateAccount | [Personal](#types.Personal) | [Account](#types.Account) | Create a new account in this node |
| GetAccounts | [Empty](#types.Empty) | [AccountList](#types.AccountList) | Return list of accounts in this node |
| LockAccount | [Personal](#types.Personal) | [Account](#types.Account) | Lock account in this node |
| UnlockAccount | [Personal](#types.Personal) | [Account](#types.Account) | Unlock account in this node |
| ImportAccount | [ImportFormat](#types.ImportFormat) | [Account](#types.Account) | Import account to this node |
| ExportAccount | [Personal](#types.Personal) | [SingleBytes](#types.SingleBytes) | Export account stored in this node |
| QueryContract | [Query](#types.Query) | [SingleBytes](#types.SingleBytes) | Query a contract method |
| QueryContractState | [StateQuery](#types.StateQuery) | [StateQueryProof](#types.StateQueryProof) | Query contract state |
| GetPeers | [Empty](#types.Empty) | [PeerList](#types.PeerList) | Return list of peers of this node and their state |
| GetVotes | [SingleBytes](#types.SingleBytes) | [VoteList](#types.VoteList) | Return list of votes |
| GetStaking | [SingleBytes](#types.SingleBytes) | [Staking](#types.Staking) | Return staking information |
| GetNameInfo | [Name](#types.Name) | [NameInfo](#types.NameInfo) | Return name information |

 <!-- end services -->


<a name="types.AccountAndRoot"></a>

### AccountAndRoot



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| Account | [bytes](#bytes) |  |  |
| Root | [bytes](#bytes) |  |  |
| Compressed | [bool](#bool) |  |  |






<a name="types.BlockHeaderList"></a>

### BlockHeaderList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| blocks | [Block](#types.Block) | repeated |  |






<a name="types.BlockMetadata"></a>

### BlockMetadata



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| header | [BlockHeader](#types.BlockHeader) |  |  |
| txcount | [int32](#int32) |  |  |






<a name="types.BlockMetadataList"></a>

### BlockMetadataList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| blocks | [BlockMetadata](#types.BlockMetadata) | repeated |  |






<a name="types.BlockchainStatus"></a>

### BlockchainStatus
BlockchainStatus is current status of blockchain


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| best_block_hash | [bytes](#bytes) |  |  |
| best_height | [uint64](#uint64) |  |  |






<a name="types.CommitResult"></a>

### CommitResult



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| error | [CommitStatus](#types.CommitStatus) |  |  |
| detail | [string](#string) |  |  |






<a name="types.CommitResultList"></a>

### CommitResultList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| results | [CommitResult](#types.CommitResult) | repeated |  |






<a name="types.Empty"></a>

### Empty







<a name="types.ImportFormat"></a>

### ImportFormat



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| wif | [SingleBytes](#types.SingleBytes) |  |  |
| oldpass | [string](#string) |  |  |
| newpass | [string](#string) |  |  |






<a name="types.Input"></a>

### Input



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| address | [bytes](#bytes) | repeated |  |
| value | [bytes](#bytes) |  |  |
| script | [bytes](#bytes) |  |  |






<a name="types.ListParams"></a>

### ListParams



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| height | [uint64](#uint64) |  |  |
| size | [uint32](#uint32) |  |  |
| offset | [uint32](#uint32) |  |  |
| asc | [bool](#bool) |  |  |






<a name="types.Name"></a>

### Name



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  |  |






<a name="types.NameInfo"></a>

### NameInfo



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [Name](#types.Name) |  |  |
| owner | [bytes](#bytes) |  |  |






<a name="types.NodeReq"></a>

### NodeReq



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| timeout | [bytes](#bytes) |  |  |
| component | [bytes](#bytes) |  |  |






<a name="types.Output"></a>

### Output



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| index | [uint32](#uint32) |  |  |
| address | [bytes](#bytes) |  |  |
| value | [bytes](#bytes) |  |  |
| script | [bytes](#bytes) |  |  |






<a name="types.Peer"></a>

### Peer



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| address | [PeerAddress](#types.PeerAddress) |  |  |
| bestblock | [NewBlockNotice](#types.NewBlockNotice) |  |  |
| state | [int32](#int32) |  |  |
| hidden | [bool](#bool) |  |  |






<a name="types.PeerList"></a>

### PeerList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| peers | [Peer](#types.Peer) | repeated |  |






<a name="types.Personal"></a>

### Personal



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| passphrase | [string](#string) |  |  |
| account | [Account](#types.Account) |  |  |






<a name="types.SingleBytes"></a>

### SingleBytes



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| value | [bytes](#bytes) |  |  |






<a name="types.Staking"></a>

### Staking



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| amount | [bytes](#bytes) |  |  |
| when | [uint64](#uint64) |  |  |






<a name="types.VerifyResult"></a>

### VerifyResult



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| tx | [Tx](#types.Tx) |  |  |
| error | [VerifyStatus](#types.VerifyStatus) |  |  |






<a name="types.Vote"></a>

### Vote



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| candidate | [bytes](#bytes) |  |  |
| amount | [bytes](#bytes) |  |  |






<a name="types.VoteList"></a>

### VoteList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| votes | [Vote](#types.Vote) | repeated |  |





 <!-- end messages -->


<a name="types.CommitStatus"></a>

### CommitStatus


| Name | Number | Description |
| ---- | ------ | ----------- |
| TX_OK | 0 |  |
| TX_NONCE_TOO_LOW | 1 |  |
| TX_ALREADY_EXISTS | 2 |  |
| TX_INVALID_HASH | 3 |  |
| TX_INVALID_SIGN | 4 |  |
| TX_INVALID_FORMAT | 5 |  |
| TX_INSUFFICIENT_BALANCE | 6 |  |
| TX_HAS_SAME_NONCE | 7 |  |
| TX_INTERNAL_ERROR | 9 |  |



<a name="types.VerifyStatus"></a>

### VerifyStatus


| Name | Number | Description |
| ---- | ------ | ----------- |
| VERIFY_STATUS_OK | 0 |  |
| VERIFY_STATUS_SIGN_NOT_MATCH | 1 |  |
| VERIFY_STATUS_INVALID_HASH | 2 | TODO: not yet impl |


 <!-- end enums -->

 <!-- end HasExtensions -->





<a name="blockchain.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## blockchain.proto


 <!-- end services -->


<a name="types.ABI"></a>

### ABI



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| version | [string](#string) |  |  |
| language | [string](#string) |  |  |
| functions | [Function](#types.Function) | repeated |  |
| state_variables | [StateVar](#types.StateVar) | repeated |  |






<a name="types.Block"></a>

### Block



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| header | [BlockHeader](#types.BlockHeader) |  |  |
| body | [BlockBody](#types.BlockBody) |  |  |






<a name="types.BlockBody"></a>

### BlockBody



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| txs | [Tx](#types.Tx) | repeated |  |






<a name="types.BlockHeader"></a>

### BlockHeader



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| chainID | [bytes](#bytes) |  | chain identifier |
| prevBlockHash | [bytes](#bytes) |  | hash of previous block |
| blockNo | [uint64](#uint64) |  | block number |
| timestamp | [int64](#int64) |  | block creation time stamp |
| blocksRootHash | [bytes](#bytes) |  | hash of root of block merkle tree |
| txsRootHash | [bytes](#bytes) |  | hash of root of transaction merkle tree |
| receiptsRootHash | [bytes](#bytes) |  | hash of root of receipt merkle tree |
| confirms | [uint64](#uint64) |  | number of blocks this block is able to confirm |
| pubKey | [bytes](#bytes) |  | block producer's public key |
| coinbaseAccount | [bytes](#bytes) |  | address of account to receive fees |
| sign | [bytes](#bytes) |  | block producer's signature of BlockHeader |






<a name="types.ContractVarProof"></a>

### ContractVarProof



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| value | [bytes](#bytes) |  |  |
| inclusion | [bool](#bool) |  |  |
| proofKey | [bytes](#bytes) |  |  |
| proofVal | [bytes](#bytes) |  |  |
| bitmap | [bytes](#bytes) |  |  |
| height | [uint32](#uint32) |  |  |
| auditPath | [bytes](#bytes) | repeated |  |






<a name="types.FnArgument"></a>

### FnArgument



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  |  |






<a name="types.Function"></a>

### Function



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  |  |
| arguments | [FnArgument](#types.FnArgument) | repeated |  |






<a name="types.Query"></a>

### Query



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| contractAddress | [bytes](#bytes) |  |  |
| queryinfo | [bytes](#bytes) |  |  |






<a name="types.Receipt"></a>

### Receipt



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| contractAddress | [bytes](#bytes) |  |  |
| status | [string](#string) |  |  |
| ret | [string](#string) |  |  |






<a name="types.State"></a>

### State



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| nonce | [uint64](#uint64) |  |  |
| balance | [bytes](#bytes) |  |  |
| codeHash | [bytes](#bytes) |  |  |
| storageRoot | [bytes](#bytes) |  |  |
| sqlRecoveryPoint | [uint64](#uint64) |  |  |






<a name="types.StateProof"></a>

### StateProof



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| state | [State](#types.State) |  |  |
| inclusion | [bool](#bool) |  |  |
| proofKey | [bytes](#bytes) |  |  |
| proofVal | [bytes](#bytes) |  |  |
| bitmap | [bytes](#bytes) |  |  |
| height | [uint32](#uint32) |  |  |
| auditPath | [bytes](#bytes) | repeated |  |






<a name="types.StateQuery"></a>

### StateQuery



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| contractAddress | [bytes](#bytes) |  |  |
| varName | [string](#string) |  |  |
| varIndex | [string](#string) |  |  |
| root | [bytes](#bytes) |  |  |
| compressed | [bool](#bool) |  |  |






<a name="types.StateQueryProof"></a>

### StateQueryProof



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| contractProof | [StateProof](#types.StateProof) |  |  |
| varProof | [ContractVarProof](#types.ContractVarProof) |  |  |






<a name="types.StateVar"></a>

### StateVar



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  |  |
| type | [string](#string) |  |  |






<a name="types.Tx"></a>

### Tx



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| body | [TxBody](#types.TxBody) |  |  |






<a name="types.TxBody"></a>

### TxBody



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| nonce | [uint64](#uint64) |  | increasing number used only once per sender account |
| account | [bytes](#bytes) |  | decoded account address |
| recipient | [bytes](#bytes) |  | decoded account address |
| amount | [bytes](#bytes) |  | variable-length big integer |
| payload | [bytes](#bytes) |  |  |
| limit | [uint64](#uint64) |  | currently not used |
| price | [bytes](#bytes) |  | variable-length big integer. currently not used |
| type | [TxType](#types.TxType) |  |  |
| sign | [bytes](#bytes) |  | sender's signature for this TxBody |






<a name="types.TxIdx"></a>

### TxIdx
TxIdx specifies a transaction's block hash and index within the block body


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| blockHash | [bytes](#bytes) |  |  |
| idx | [int32](#int32) |  |  |






<a name="types.TxInBlock"></a>

### TxInBlock



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| txIdx | [TxIdx](#types.TxIdx) |  |  |
| tx | [Tx](#types.Tx) |  |  |






<a name="types.TxList"></a>

### TxList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| txs | [Tx](#types.Tx) | repeated |  |





 <!-- end messages -->


<a name="types.TxType"></a>

### TxType


| Name | Number | Description |
| ---- | ------ | ----------- |
| NORMAL | 0 |  |
| GOVERNANCE | 1 |  |


 <!-- end enums -->

 <!-- end HasExtensions -->





<a name="metric.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## metric.proto


 <!-- end services -->


<a name="types.Metrics"></a>

### Metrics



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| peers | [PeerMetric](#types.PeerMetric) | repeated |  |






<a name="types.MetricsRequest"></a>

### MetricsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| types | [MetricType](#types.MetricType) | repeated |  |






<a name="types.PeerMetric"></a>

### PeerMetric



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| peerID | [bytes](#bytes) |  |  |
| sumIn | [int64](#int64) |  |  |
| avrIn | [int64](#int64) |  |  |
| sumOut | [int64](#int64) |  |  |
| avrOut | [int64](#int64) |  |  |





 <!-- end messages -->


<a name="types.MetricType"></a>

### MetricType


| Name | Number | Description |
| ---- | ------ | ----------- |
| NOTHING | 0 | NOTHING should not be used. |
| P2P_NETWORK | 1 | Metric for p2p network transfer |


 <!-- end enums -->

 <!-- end HasExtensions -->





## Scalar Value Types

| .proto Type | Notes | C++ Type | Java Type | Python Type |
| ----------- | ----- | -------- | --------- | ----------- |
| <a name="double" /> double |  | double | double | float |
| <a name="float" /> float |  | float | float | float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long |
| <a name="bool" /> bool |  | bool | boolean | boolean |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str |
