
## ibc/applications/transfer/v1/transfer.proto

### DenomTrace

DenomTrace contains the base denomination for ICS20 fungible tokens and the source tracing information path.

| Field        | Type                           | Label | Description                                                                                           |
| ------------ | ------------------------------ | ----- | ----------------------------------------------------------------------------------------------------- |
| `path`       | [string](value.md#string) |       | path defines the chain of port/channel identifiers used for tracing the source of the fungible token. |
| `base_denom` | [string](value.md#string) |       | base denomination of the relayed fungible token.                                                      |

### FungibleTokenPacketData

FungibleTokenPacketData defines a struct for the packet payload See FungibleTokenPacketData spec: https://github.com/cosmos/ics/tree/master/spec/ics-020-fungible-token-transfer#data-structures

| Field      | Type                           | Label | Description                                    |
| ---------- | ------------------------------ | ----- | ---------------------------------------------- |
| `denom`    | [string](value.md#string) |       | the token denomination to be transferred       |
| `amount`   | [uint64](value.md#uint64) |       | the token amount to be transferred             |
| `sender`   | [string](value.md#string) |       | the sender address                             |
| `receiver` | [string](value.md#string) |       | the recipient address on the destination chain |

### Params

Params defines the set of IBC transfer parameters. NOTE: To prevent a single token from being transferred, set the TransfersEnabled parameter to true and then set the bank module's SendEnabled parameter for the denomination to false.

| Field             | Type                       | Label | Description                                                                         |
| ----------------- | -------------------------- | ----- | ----------------------------------------------------------------------------------- |
| `send_enabled`    | [bool](value.md#bool) |       | send_enabled enables or disables all cross-chain token transfers from this chain.  |
| `receive_enabled` | [bool](value.md#bool) |       | receive_enabled enables or disables all cross-chain token transfers to this chain. |



## ibc/applications/transfer/v1/genesis.proto

### GenesisState

GenesisState defines the ibc-transfer genesis state

| Field          | Type                                                                | Label    | Description |
| -------------- | ------------------------------------------------------------------- | -------- | ----------- |
| `port_id`      | [string](value.md#string)                                      |          |             |
| `denom_traces` | [DenomTrace](ibc.md#ibc.applications.transfer.v1.DenomTrace) | repeated |             |
| `params`       | [Params](ibc.md#ibc.applications.transfer.v1.Params)         |          |             |



## ibc/applications/transfer/v1/query.proto

### QueryDenomTraceRequest

QueryDenomTraceRequest is the request type for the Query/DenomTrace RPC method

| Field  | Type                           | Label | Description                                                 |
| ------ | ------------------------------ | ----- | ----------------------------------------------------------- |
| `hash` | [string](value.md#string) |       | hash (in hex format) of the denomination trace information. |

### QueryDenomTraceResponse

QueryDenomTraceResponse is the response type for the Query/DenomTrace RPC method.

| Field         | Type                                                                | Label | Description                                                        |
| ------------- | ------------------------------------------------------------------- | ----- | ------------------------------------------------------------------ |
| `denom_trace` | [DenomTrace](ibc.md#ibc.applications.transfer.v1.DenomTrace) |       | denom_trace returns the requested denomination trace information. |

### QueryDenomTracesRequest

QueryConnectionsRequest is the request type for the Query/DenomTraces RPC method

| Field        | Type                                                                                         | Label | Description                                                |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryDenomTracesResponse

QueryConnectionsResponse is the response type for the Query/DenomTraces RPC method.

| Field          | Type                                                                                           | Label    | Description                                                |
| -------------- | ---------------------------------------------------------------------------------------------- | -------- | ---------------------------------------------------------- |
| `denom_traces` | [DenomTrace](ibc.md#ibc.applications.transfer.v1.DenomTrace)                            | repeated | denom_traces returns all denominations trace information. |
| `pagination`   | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response.         |

### QueryParamsRequest

QueryParamsRequest is the request type for the Query/Params RPC method.

### QueryParamsResponse

QueryParamsResponse is the response type for the Query/Params RPC method.

| Field    | Type                                                        | Label | Description                                  |
| -------- | ----------------------------------------------------------- | ----- | -------------------------------------------- |
| `params` | [Params](ibc.md#ibc.applications.transfer.v1.Params) |       | params defines the parameters of the module. |

### Query

Query provides defines the gRPC querier service.

| Method Name   | Request Type                                                                                  | Response Type                                                                                   | Description                                               | HTTP Verb | Endpoint                                                |
| ------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | --------------------------------------------------------- | --------- | ------------------------------------------------------- |
| `DenomTrace`  | [QueryDenomTraceRequest](ibc.md#ibc.applications.transfer.v1.QueryDenomTraceRequest)   | [QueryDenomTraceResponse](ibc.md#ibc.applications.transfer.v1.QueryDenomTraceResponse)   | DenomTrace queries a denomination trace information.      | GET       | /ibc/applications/transfer/v1beta1/denom_traces/{hash} |
| `DenomTraces` | [QueryDenomTracesRequest](ibc.md#ibc.applications.transfer.v1.QueryDenomTracesRequest) | [QueryDenomTracesResponse](ibc.md#ibc.applications.transfer.v1.QueryDenomTracesResponse) | DenomTraces queries all denomination traces.              | GET       | /ibc/applications/transfer/v1beta1/denom_traces        |
| `Params`      | [QueryParamsRequest](ibc.md#ibc.applications.transfer.v1.QueryParamsRequest)           | [QueryParamsResponse](ibc.md#ibc.applications.transfer.v1.QueryParamsResponse)           | Params queries all parameters of the ibc-transfer module. | GET       | /ibc/applications/transfer/v1beta1/params               |



## ibc/core/client/v1/client.proto

### ClientConsensusStates

ClientConsensusStates defines all the stored consensus states for a given client.

| Field              | Type                                                                                  | Label    | Description                                                   |
| ------------------ | ------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------- |
| `client_id`        | [string](value.md#string)                                                        |          | client identifier                                             |
| `consensus_states` | [ConsensusStateWithHeight](ibc.md#ibc.core.client.v1.ConsensusStateWithHeight) | repeated | consensus states and their heights associated with the client |

### ClientUpdateProposal

ClientUpdateProposal is a governance proposal. If it passes, the client is updated with the provided header. The update may fail if the header is not valid given certain conditions specified by the client implementation.

| Field         | Type                                                     | Label | Description                                                               |
| ------------- | -------------------------------------------------------- | ----- | ------------------------------------------------------------------------- |
| `title`       | [string](value.md#string)                           |       | the title of the update proposal                                          |
| `description` | [string](value.md#string)                           |       | the description of the proposal                                           |
| `client_id`   | [string](value.md#string)                           |       | the client identifier for the client to be updated if the proposal passes |
| `header`      | google.protobuf.Any |       | the header used to update the client if the proposal passes               |

### ConsensusStateWithHeight

ConsensusStateWithHeight defines a consensus state with an additional height field.

| Field             | Type                                                     | Label | Description            |
| ----------------- | -------------------------------------------------------- | ----- | ---------------------- |
| `height`          | [Height](ibc.md#ibc.core.client.v1.Height)        |       | consensus state height |
| `consensus_state` | google.protobuf.Any |       | consensus state        |

### Height

Height is a monotonically increasing data type that can be compared against another Height for the purposes of updating and freezing clients

Normally the RevisionHeight is incremented at each height while keeping RevisionNumber the same. However some consensus algorithms may choose to reset the height in certain conditions e.g. hard forks, state-machine breaking changes In these cases, the RevisionNumber is incremented so that height continues to be monitonically increasing even as the RevisionHeight gets reset

| Field             | Type                           | Label | Description                                  |
| ----------------- | ------------------------------ | ----- | -------------------------------------------- |
| `revision_number` | [uint64](value.md#uint64) |       | the revision that the client is currently on |
| `revision_height` | [uint64](value.md#uint64) |       | the height within the given revision         |

### IdentifiedClientState

IdentifiedClientState defines a client state with an additional client identifier field.

| Field          | Type                                                     | Label | Description       |
| -------------- | -------------------------------------------------------- | ----- | ----------------- |
| `client_id`    | [string](value.md#string)                           |       | client identifier |
| `client_state` | google.protobuf.Any |       | client state      |

### Params

Params defines the set of IBC light client parameters.

| Field             | Type                           | Label    | Description                                                      |
| ----------------- | ------------------------------ | -------- | ---------------------------------------------------------------- |
| `allowed_clients` | [string](value.md#string) | repeated | allowed_clients defines the list of allowed client state types. |



## ibc/applications/transfer/v1/tx.proto

### MsgTransfer

MsgTransfer defines a msg to transfer fungible tokens (i.e Coins) between ICS20 enabled chains. See ICS Spec here: https://github.com/cosmos/ics/tree/master/spec/ics-020-fungible-token-transfer#data-structures

| Field               | Type                                                                 | Label | Description                                                                                                        |
| ------------------- | -------------------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------------------------ |
| `source_port`       | [string](value.md#string)                                       |       | the port on which the packet will be sent                                                                          |
| `source_channel`    | [string](value.md#string)                                       |       | the channel by which the packet will be sent                                                                       |
| `token`             | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin)   |       | the tokens to be transferred                                                                                       |
| `sender`            | [string](value.md#string)                                       |       | the sender address                                                                                                 |
| `receiver`          | [string](value.md#string)                                       |       | the recipient address on the destination chain                                                                     |
| `timeout_height`    | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | Timeout height relative to the current block height. The timeout is disabled when set to 0.                        |
| `timeout_timestamp` | [uint64](value.md#uint64)                                       |       | Timeout timestamp (in nanoseconds) relative to the current block timestamp. The timeout is disabled when set to 0. |

### MsgTransferResponse

MsgTransferResponse defines the Msg/Transfer response type.

### Msg

Msg defines the ibc/transfer Msg service.

| Method Name | Request Type                                                          | Response Type                                                                         | Description                                            | HTTP Verb | Endpoint |
| ----------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------ | --------- | -------- |
| `Transfer`  | [MsgTransfer](ibc.md#ibc.applications.transfer.v1.MsgTransfer) | [MsgTransferResponse](ibc.md#ibc.applications.transfer.v1.MsgTransferResponse) | Transfer defines a rpc handler method for MsgTransfer. |           |          |



## ibc/core/channel/v1/channel.proto

### Acknowledgement

Acknowledgement is the recommended acknowledgement format to be used by app-specific protocols. NOTE: The field numbers 21 and 22 were explicitly chosen to avoid accidental conflicts with other protobuf message formats used for acknowledgements. The first byte of any message with this format will be the non-ASCII values `0xaa` (result) or `0xb2` (error). Implemented as defined by ICS: https://github.com/cosmos/ics/tree/master/spec/ics-004-channel-and-packet-semantics#acknowledgement-envelope

| Field    | Type                           | Label | Description |
| -------- | ------------------------------ | ----- | ----------- |
| `result` | [bytes](value.md#bytes)   |       |             |
| `error`  | [string](value.md#string) |       |             |

### Channel

Channel defines pipeline for exactly-once packet delivery between specific modules on separate blockchains, which has at least one end capable of sending packets and one end capable of receiving packets.

| Field             | Type                                                           | Label    | Description                                                                                    |
| ----------------- | -------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------- |
| `state`           | [State](ibc.md#ibc.core.channel.v1.State)               |          | current state of the channel end                                                               |
| `ordering`        | [Order](ibc.md#ibc.core.channel.v1.Order)               |          | whether the channel is ordered or unordered                                                    |
| `counterparty`    | [Counterparty](ibc.md#ibc.core.channel.v1.Counterparty) |          | counterparty channel end                                                                       |
| `connection_hops` | [string](value.md#string)                                 | repeated | list of connection identifiers, in order, along which packets sent on this channel will travel |
| `version`         | [string](value.md#string)                                 |          | opaque channel version, which is agreed upon during the handshake                              |

### Counterparty

Counterparty defines a channel end counterparty

| Field        | Type                           | Label | Description                                                             |
| ------------ | ------------------------------ | ----- | ----------------------------------------------------------------------- |
| `port_id`    | [string](value.md#string) |       | port on the counterparty chain which owns the other end of the channel. |
| `channel_id` | [string](value.md#string) |       | channel end on the counterparty chain                                   |

### IdentifiedChannel

IdentifiedChannel defines a channel with additional port and channel identifier fields.

| Field             | Type                                                           | Label    | Description                                                                                    |
| ----------------- | -------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------- |
| `state`           | [State](ibc.md#ibc.core.channel.v1.State)               |          | current state of the channel end                                                               |
| `ordering`        | [Order](ibc.md#ibc.core.channel.v1.Order)               |          | whether the channel is ordered or unordered                                                    |
| `counterparty`    | [Counterparty](ibc.md#ibc.core.channel.v1.Counterparty) |          | counterparty channel end                                                                       |
| `connection_hops` | [string](value.md#string)                                 | repeated | list of connection identifiers, in order, along which packets sent on this channel will travel |
| `version`         | [string](value.md#string)                                 |          | opaque channel version, which is agreed upon during the handshake                              |
| `port_id`         | [string](value.md#string)                                 |          | port identifier                                                                                |
| `channel_id`      | [string](value.md#string)                                 |          | channel identifier                                                                             |

### Packet

Packet defines a type that carries data across different chains through IBC

| Field                 | Type                                                                 | Label | Description                                                                                                                                                                   |
| --------------------- | -------------------------------------------------------------------- | ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `sequence`            | [uint64](value.md#uint64)                                       |       | number corresponds to the order of sends and receives, where a Packet with an earlier sequence number must be sent and received before a Packet with a later sequence number. |
| `source_port`         | [string](value.md#string)                                       |       | identifies the port on the sending chain.                                                                                                                                     |
| `source_channel`      | [string](value.md#string)                                       |       | identifies the channel end on the sending chain.                                                                                                                              |
| `destination_port`    | [string](value.md#string)                                       |       | identifies the port on the receiving chain.                                                                                                                                   |
| `destination_channel` | [string](value.md#string)                                       |       | identifies the channel end on the receiving chain.                                                                                                                            |
| `data`                | [bytes](value.md#bytes)                                         |       | actual opaque bytes transferred directly to the application module                                                                                                            |
| `timeout_height`      | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | block height after which the packet times out                                                                                                                                 |
| `timeout_timestamp`   | [uint64](value.md#uint64)                                       |       | block timestamp (in nanoseconds) after which the packet times out                                                                                                             |

### PacketState

PacketState defines the generic type necessary to retrieve and store packet commitments, acknowledgements, and receipts. Caller is responsible for knowing the context necessary to interpret this state as a commitment, acknowledgement, or a receipt.

| Field        | Type                           | Label | Description                                 |
| ------------ | ------------------------------ | ----- | ------------------------------------------- |
| `port_id`    | [string](value.md#string) |       | channel port identifier.                    |
| `channel_id` | [string](value.md#string) |       | channel unique identifier.                  |
| `sequence`   | [uint64](value.md#uint64) |       | packet sequence.                            |
| `data`       | [bytes](value.md#bytes)   |       | embedded data that represents packet state. |

### Order

Order defines if a channel is ORDERED or UNORDERED

| Name                     | Number | Description                                                                                     |
| ------------------------ | ------ | ----------------------------------------------------------------------------------------------- |
| ORDER_NONE_UNSPECIFIED | 0      | zero-value for channel ordering                                                                 |
| ORDER_UNORDERED         | 1      | packets can be delivered in any order, which may differ from the order in which they were sent. |
| ORDER_ORDERED           | 2      | packets are delivered exactly in the order which they were sent                                 |

### State

State defines if a channel is in one of the following states: CLOSED, INIT, TRYOPEN, OPEN or UNINITIALIZED.

| Name                              | Number | Description                                                                                 |
| --------------------------------- | ------ | ------------------------------------------------------------------------------------------- |
| STATE_UNINITIALIZED_UNSPECIFIED | 0      | Default State                                                                               |
| STATE_INIT                       | 1      | A channel has just started the opening handshake.                                           |
| STATE_TRYOPEN                    | 2      | A channel has acknowledged the handshake step on the counterparty chain.                    |
| STATE_OPEN                       | 3      | A channel has completed the handshake. Open channels are ready to send and receive packets. |
| STATE_CLOSED                     | 4      | A channel has been closed and can no longer be used to send or receive packets.             |



## ibc/core/channel/v1/genesis.proto

### GenesisState

GenesisState defines the ibc channel submodule's genesis state.

| Field                   | Type                                                                     | Label    | Description                                            |
| ----------------------- | ------------------------------------------------------------------------ | -------- | ------------------------------------------------------ |
| `channels`              | [IdentifiedChannel](ibc.md#ibc.core.channel.v1.IdentifiedChannel) | repeated |                                                        |
| `acknowledgements`      | [PacketState](ibc.md#ibc.core.channel.v1.PacketState)             | repeated |                                                        |
| `commitments`           | [PacketState](ibc.md#ibc.core.channel.v1.PacketState)             | repeated |                                                        |
| `receipts`              | [PacketState](ibc.md#ibc.core.channel.v1.PacketState)             | repeated |                                                        |
| `send_sequences`        | [PacketSequence](ibc.md#ibc.core.channel.v1.PacketSequence)       | repeated |                                                        |
| `recv_sequences`        | [PacketSequence](ibc.md#ibc.core.channel.v1.PacketSequence)       | repeated |                                                        |
| `ack_sequences`         | [PacketSequence](ibc.md#ibc.core.channel.v1.PacketSequence)       | repeated |                                                        |
| `next_channel_sequence` | [uint64](value.md#uint64)                                           |          | the sequence for the next generated channel identifier |

### PacketSequence

PacketSequence defines the genesis type necessary to retrieve and store next send and receive sequences.

| Field        | Type                           | Label | Description |
| ------------ | ------------------------------ | ----- | ----------- |
| `port_id`    | [string](value.md#string) |       |             |
| `channel_id` | [string](value.md#string) |       |             |
| `sequence`   | [uint64](value.md#uint64) |       |             |



## ibc/core/channel/v1/query.proto

### QueryChannelClientStateRequest

QueryChannelClientStateRequest is the request type for the Query/ClientState RPC method

| Field        | Type                           | Label | Description               |
| ------------ | ------------------------------ | ----- | ------------------------- |
| `port_id`    | [string](value.md#string) |       | port unique identifier    |
| `channel_id` | [string](value.md#string) |       | channel unique identifier |

### QueryChannelClientStateResponse

QueryChannelClientStateResponse is the Response type for the Query/QueryChannelClientState RPC method

| Field                     | Type                                                                                               | Label | Description                              |
| ------------------------- | -------------------------------------------------------------------------------------------------- | ----- | ---------------------------------------- |
| `identified_client_state` | [ibc.core.client.v1.IdentifiedClientState](ibc.md#ibc.core.client.v1.IdentifiedClientState) |       | client state associated with the channel |
| `proof`                   | [bytes](value.md#bytes)                                                                       |       | merkle proof of existence                |
| `proof_height`            | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)                               |       | height at which the proof was retrieved  |

### QueryChannelConsensusStateRequest

QueryChannelConsensusStateRequest is the request type for the Query/ConsensusState RPC method

| Field             | Type                           | Label | Description                            |
| ----------------- | ------------------------------ | ----- | -------------------------------------- |
| `port_id`         | [string](value.md#string) |       | port unique identifier                 |
| `channel_id`      | [string](value.md#string) |       | channel unique identifier              |
| `revision_number` | [uint64](value.md#uint64) |       | revision number of the consensus state |
| `revision_height` | [uint64](value.md#uint64) |       | revision height of the consensus state |

### QueryChannelConsensusStateResponse

QueryChannelClientStateResponse is the Response type for the Query/QueryChannelClientState RPC method

| Field             | Type                                                                 | Label | Description                                   |
| ----------------- | -------------------------------------------------------------------- | ----- | --------------------------------------------- |
| `consensus_state` | google.protobuf.Any             |       | consensus state associated with the channel   |
| `client_id`       | [string](value.md#string)                                       |       | client ID associated with the consensus state |
| `proof`           | [bytes](value.md#bytes)                                         |       | merkle proof of existence                     |
| `proof_height`    | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved       |

### QueryChannelRequest

QueryChannelRequest is the request type for the Query/Channel RPC method

| Field        | Type                           | Label | Description               |
| ------------ | ------------------------------ | ----- | ------------------------- |
| `port_id`    | [string](value.md#string) |       | port unique identifier    |
| `channel_id` | [string](value.md#string) |       | channel unique identifier |

### QueryChannelResponse

QueryChannelResponse is the response type for the Query/Channel RPC method. Besides the Channel end, it includes a proof and the height from which the proof was retrieved.

| Field          | Type                                                                 | Label | Description                                     |
| -------------- | -------------------------------------------------------------------- | ----- | ----------------------------------------------- |
| `channel`      | [Channel](ibc.md#ibc.core.channel.v1.Channel)                 |       | channel associated with the request identifiers |
| `proof`        | [bytes](value.md#bytes)                                         |       | merkle proof of existence                       |
| `proof_height` | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved         |

### QueryChannelsRequest

QueryChannelsRequest is the request type for the Query/Channels RPC method

| Field        | Type                                                                                         | Label | Description        |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ------------------ |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination request |

### QueryChannelsResponse

QueryChannelsResponse is the response type for the Query/Channels RPC method.

| Field        | Type                                                                                           | Label    | Description                           |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | ------------------------------------- |
| `channels`   | [IdentifiedChannel](ibc.md#ibc.core.channel.v1.IdentifiedChannel)                       | repeated | list of stored channels of the chain. |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination response                   |
| `height`     | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)                           |          | query block height                    |

### QueryConnectionChannelsRequest

QueryConnectionChannelsRequest is the request type for the Query/QueryConnectionChannels RPC method

| Field        | Type                                                                                         | Label | Description                  |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ---------------------------- |
| `connection` | [string](value.md#string)                                                               |       | connection unique identifier |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination request           |

### QueryConnectionChannelsResponse

QueryConnectionChannelsResponse is the Response type for the Query/QueryConnectionChannels RPC method

| Field        | Type                                                                                           | Label    | Description                                    |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | ---------------------------------------------- |
| `channels`   | [IdentifiedChannel](ibc.md#ibc.core.channel.v1.IdentifiedChannel)                       | repeated | list of channels associated with a connection. |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination response                            |
| `height`     | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)                           |          | query block height                             |

### QueryNextSequenceReceiveRequest

QueryNextSequenceReceiveRequest is the request type for the Query/QueryNextSequenceReceiveRequest RPC method

| Field        | Type                           | Label | Description               |
| ------------ | ------------------------------ | ----- | ------------------------- |
| `port_id`    | [string](value.md#string) |       | port unique identifier    |
| `channel_id` | [string](value.md#string) |       | channel unique identifier |

### QueryNextSequenceReceiveResponse

QuerySequenceResponse is the request type for the Query/QueryNextSequenceReceiveResponse RPC method

| Field                   | Type                                                                 | Label | Description                             |
| ----------------------- | -------------------------------------------------------------------- | ----- | --------------------------------------- |
| `next_sequence_receive` | [uint64](value.md#uint64)                                       |       | next sequence receive number            |
| `proof`                 | [bytes](value.md#bytes)                                         |       | merkle proof of existence               |
| `proof_height`          | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved |

### QueryPacketAcknowledgementRequest

QueryPacketAcknowledgementRequest is the request type for the Query/PacketAcknowledgement RPC method

| Field        | Type                           | Label | Description               |
| ------------ | ------------------------------ | ----- | ------------------------- |
| `port_id`    | [string](value.md#string) |       | port unique identifier    |
| `channel_id` | [string](value.md#string) |       | channel unique identifier |
| `sequence`   | [uint64](value.md#uint64) |       | packet sequence           |

### QueryPacketAcknowledgementResponse

QueryPacketAcknowledgementResponse defines the client query response for a packet which also includes a proof and the height from which the proof was retrieved

| Field             | Type                                                                 | Label | Description                               |
| ----------------- | -------------------------------------------------------------------- | ----- | ----------------------------------------- |
| `acknowledgement` | [bytes](value.md#bytes)                                         |       | packet associated with the request fields |
| `proof`           | [bytes](value.md#bytes)                                         |       | merkle proof of existence                 |
| `proof_height`    | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved   |

### QueryPacketAcknowledgementsRequest

QueryPacketAcknowledgementsRequest is the request type for the Query/QueryPacketCommitments RPC method

| Field        | Type                                                                                         | Label | Description               |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ------------------------- |
| `port_id`    | [string](value.md#string)                                                               |       | port unique identifier    |
| `channel_id` | [string](value.md#string)                                                               |       | channel unique identifier |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination request        |

### QueryPacketAcknowledgementsResponse

QueryPacketAcknowledgemetsResponse is the request type for the Query/QueryPacketAcknowledgements RPC method

| Field              | Type                                                                                           | Label    | Description         |
| ------------------ | ---------------------------------------------------------------------------------------------- | -------- | ------------------- |
| `acknowledgements` | [PacketState](ibc.md#ibc.core.channel.v1.PacketState)                                   | repeated |                     |
| `pagination`       | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination response |
| `height`           | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)                           |          | query block height  |

### QueryPacketCommitmentRequest

QueryPacketCommitmentRequest is the request type for the Query/PacketCommitment RPC method

| Field        | Type                           | Label | Description               |
| ------------ | ------------------------------ | ----- | ------------------------- |
| `port_id`    | [string](value.md#string) |       | port unique identifier    |
| `channel_id` | [string](value.md#string) |       | channel unique identifier |
| `sequence`   | [uint64](value.md#uint64) |       | packet sequence           |

### QueryPacketCommitmentResponse

QueryPacketCommitmentResponse defines the client query response for a packet which also includes a proof and the height from which the proof was retrieved

| Field          | Type                                                                 | Label | Description                               |
| -------------- | -------------------------------------------------------------------- | ----- | ----------------------------------------- |
| `commitment`   | [bytes](value.md#bytes)                                         |       | packet associated with the request fields |
| `proof`        | [bytes](value.md#bytes)                                         |       | merkle proof of existence                 |
| `proof_height` | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved   |

### QueryPacketCommitmentsRequest

QueryPacketCommitmentsRequest is the request type for the Query/QueryPacketCommitments RPC method

| Field        | Type                                                                                         | Label | Description               |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ------------------------- |
| `port_id`    | [string](value.md#string)                                                               |       | port unique identifier    |
| `channel_id` | [string](value.md#string)                                                               |       | channel unique identifier |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination request        |

### QueryPacketCommitmentsResponse

QueryPacketCommitmentsResponse is the request type for the Query/QueryPacketCommitments RPC method

| Field         | Type                                                                                           | Label    | Description         |
| ------------- | ---------------------------------------------------------------------------------------------- | -------- | ------------------- |
| `commitments` | [PacketState](ibc.md#ibc.core.channel.v1.PacketState)                                   | repeated |                     |
| `pagination`  | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination response |
| `height`      | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)                           |          | query block height  |

### QueryPacketReceiptRequest

QueryPacketReceiptRequest is the request type for the Query/PacketReceipt RPC method

| Field        | Type                           | Label | Description               |
| ------------ | ------------------------------ | ----- | ------------------------- |
| `port_id`    | [string](value.md#string) |       | port unique identifier    |
| `channel_id` | [string](value.md#string) |       | channel unique identifier |
| `sequence`   | [uint64](value.md#uint64) |       | packet sequence           |

### QueryPacketReceiptResponse

QueryPacketReceiptResponse defines the client query response for a packet receipt which also includes a proof, and the height from which the proof was retrieved

| Field          | Type                                                                 | Label | Description                             |
| -------------- | -------------------------------------------------------------------- | ----- | --------------------------------------- |
| `received`     | [bool](value.md#bool)                                           |       | success flag for if receipt exists      |
| `proof`        | [bytes](value.md#bytes)                                         |       | merkle proof of existence               |
| `proof_height` | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved |

### QueryUnreceivedAcksRequest

QueryUnreceivedAcks is the request type for the Query/UnreceivedAcks RPC method

| Field                  | Type                           | Label    | Description                       |
| ---------------------- | ------------------------------ | -------- | --------------------------------- |
| `port_id`              | [string](value.md#string) |          | port unique identifier            |
| `channel_id`           | [string](value.md#string) |          | channel unique identifier         |
| `packet_ack_sequences` | [uint64](value.md#uint64) | repeated | list of acknowledgement sequences |

### QueryUnreceivedAcksResponse

QueryUnreceivedAcksResponse is the response type for the Query/UnreceivedAcks RPC method

| Field       | Type                                                                 | Label    | Description                                  |
| ----------- | -------------------------------------------------------------------- | -------- | -------------------------------------------- |
| `sequences` | [uint64](value.md#uint64)                                       | repeated | list of unreceived acknowledgement sequences |
| `height`    | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |          | query block height                           |

### QueryUnreceivedPacketsRequest

QueryUnreceivedPacketsRequest is the request type for the Query/UnreceivedPackets RPC method

| Field                         | Type                           | Label    | Description               |
| ----------------------------- | ------------------------------ | -------- | ------------------------- |
| `port_id`                     | [string](value.md#string) |          | port unique identifier    |
| `channel_id`                  | [string](value.md#string) |          | channel unique identifier |
| `packet_commitment_sequences` | [uint64](value.md#uint64) | repeated | list of packet sequences  |

### QueryUnreceivedPacketsResponse

QueryUnreceivedPacketsResponse is the response type for the Query/UnreceivedPacketCommitments RPC method

| Field       | Type                                                                 | Label    | Description                         |
| ----------- | -------------------------------------------------------------------- | -------- | ----------------------------------- |
| `sequences` | [uint64](value.md#uint64)                                       | repeated | list of unreceived packet sequences |
| `height`    | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |          | query block height                  |

### Query

Query provides defines the gRPC querier service

| Method Name              | Request Type                                                                                               | Response Type                                                                                                | Description                                                                                                             | HTTP Verb | Endpoint                                                                                                                                  |
| ------------------------ | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `Channel`                | [QueryChannelRequest](ibc.md#ibc.core.channel.v1.QueryChannelRequest)                               | [QueryChannelResponse](ibc.md#ibc.core.channel.v1.QueryChannelResponse)                               | Channel queries an IBC Channel.                                                                                         | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}                                                                         |
| `Channels`               | [QueryChannelsRequest](ibc.md#ibc.core.channel.v1.QueryChannelsRequest)                             | [QueryChannelsResponse](ibc.md#ibc.core.channel.v1.QueryChannelsResponse)                             | Channels queries all the IBC channels of a chain.                                                                       | GET       | /ibc/core/channel/v1beta1/channels                                                                                                        |
| `ConnectionChannels`     | [QueryConnectionChannelsRequest](ibc.md#ibc.core.channel.v1.QueryConnectionChannelsRequest)         | [QueryConnectionChannelsResponse](ibc.md#ibc.core.channel.v1.QueryConnectionChannelsResponse)         | ConnectionChannels queries all the channels associated with a connection end.                                           | GET       | /ibc/core/channel/v1beta1/connections/{connection}/channels                                                                               |
| `ChannelClientState`     | [QueryChannelClientStateRequest](ibc.md#ibc.core.channel.v1.QueryChannelClientStateRequest)         | [QueryChannelClientStateResponse](ibc.md#ibc.core.channel.v1.QueryChannelClientStateResponse)         | ChannelClientState queries for the client state for the channel associated with the provided channel identifiers.       | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/client_state                                                           |
| `ChannelConsensusState`  | [QueryChannelConsensusStateRequest](ibc.md#ibc.core.channel.v1.QueryChannelConsensusStateRequest)   | [QueryChannelConsensusStateResponse](ibc.md#ibc.core.channel.v1.QueryChannelConsensusStateResponse)   | ChannelConsensusState queries for the consensus state for the channel associated with the provided channel identifiers. | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/consensus_state/revision/{revision_number}/height/{revision_height}  |
| `PacketCommitment`       | [QueryPacketCommitmentRequest](ibc.md#ibc.core.channel.v1.QueryPacketCommitmentRequest)             | [QueryPacketCommitmentResponse](ibc.md#ibc.core.channel.v1.QueryPacketCommitmentResponse)             | PacketCommitment queries a stored packet commitment hash.                                                               | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/packet_commitments/{sequence}                                          |
| `PacketCommitments`      | [QueryPacketCommitmentsRequest](ibc.md#ibc.core.channel.v1.QueryPacketCommitmentsRequest)           | [QueryPacketCommitmentsResponse](ibc.md#ibc.core.channel.v1.QueryPacketCommitmentsResponse)           | PacketCommitments returns all the packet commitments hashes associated with a channel.                                  | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/packet_commitments                                                     |
| `PacketReceipt`          | [QueryPacketReceiptRequest](ibc.md#ibc.core.channel.v1.QueryPacketReceiptRequest)                   | [QueryPacketReceiptResponse](ibc.md#ibc.core.channel.v1.QueryPacketReceiptResponse)                   | PacketReceipt queries if a given packet sequence has been received on the queried chain                                 | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/packet_receipts/{sequence}                                             |
| `PacketAcknowledgement`  | [QueryPacketAcknowledgementRequest](ibc.md#ibc.core.channel.v1.QueryPacketAcknowledgementRequest)   | [QueryPacketAcknowledgementResponse](ibc.md#ibc.core.channel.v1.QueryPacketAcknowledgementResponse)   | PacketAcknowledgement queries a stored packet acknowledgement hash.                                                     | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/packet_acks/{sequence}                                                 |
| `PacketAcknowledgements` | [QueryPacketAcknowledgementsRequest](ibc.md#ibc.core.channel.v1.QueryPacketAcknowledgementsRequest) | [QueryPacketAcknowledgementsResponse](ibc.md#ibc.core.channel.v1.QueryPacketAcknowledgementsResponse) | PacketAcknowledgements returns all the packet acknowledgements associated with a channel.                               | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/packet_acknowledgements                                                |
| `UnreceivedPackets`      | [QueryUnreceivedPacketsRequest](ibc.md#ibc.core.channel.v1.QueryUnreceivedPacketsRequest)           | [QueryUnreceivedPacketsResponse](ibc.md#ibc.core.channel.v1.QueryUnreceivedPacketsResponse)           | UnreceivedPackets returns all the unreceived IBC packets associated with a channel and sequences.                       | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/packet_commitments/{packet_commitment_sequences}/unreceived_packets |
| `UnreceivedAcks`         | [QueryUnreceivedAcksRequest](ibc.md#ibc.core.channel.v1.QueryUnreceivedAcksRequest)                 | [QueryUnreceivedAcksResponse](ibc.md#ibc.core.channel.v1.QueryUnreceivedAcksResponse)                 | UnreceivedAcks returns all the unreceived IBC acknowledgements associated with a channel and sequences.                 | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/packet_commitments/{packet_ack_sequences}/unreceived_acks           |
| `NextSequenceReceive`    | [QueryNextSequenceReceiveRequest](ibc.md#ibc.core.channel.v1.QueryNextSequenceReceiveRequest)       | [QueryNextSequenceReceiveResponse](ibc.md#ibc.core.channel.v1.QueryNextSequenceReceiveResponse)       | NextSequenceReceive returns the next receive sequence for a given channel.                                              | GET       | /ibc/core/channel/v1beta1/channels/{channel_id}/ports/{port_id}/next_sequence                                                          |



## ibc/core/channel/v1/tx.proto

### MsgAcknowledgement

MsgAcknowledgement receives incoming IBC acknowledgement

| Field             | Type                                                                 | Label | Description |
| ----------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `packet`          | [Packet](ibc.md#ibc.core.channel.v1.Packet)                   |       |             |
| `acknowledgement` | [bytes](value.md#bytes)                                         |       |             |
| `proof_acked`     | [bytes](value.md#bytes)                                         |       |             |
| `proof_height`    | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |             |
| `signer`          | [string](value.md#string)                                       |       |             |

### MsgAcknowledgementResponse

MsgAcknowledgementResponse defines the Msg/Acknowledgement response type.

### MsgChannelCloseConfirm

MsgChannelCloseConfirm defines a msg sent by a Relayer to Chain B to acknowledge the change of channel state to CLOSED on Chain A.

| Field          | Type                                                                 | Label | Description |
| -------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `port_id`      | [string](value.md#string)                                       |       |             |
| `channel_id`   | [string](value.md#string)                                       |       |             |
| `proof_init`   | [bytes](value.md#bytes)                                         |       |             |
| `proof_height` | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |             |
| `signer`       | [string](value.md#string)                                       |       |             |

### MsgChannelCloseConfirmResponse

MsgChannelCloseConfirmResponse defines the Msg/ChannelCloseConfirm response type.

### MsgChannelCloseInit

MsgChannelCloseInit defines a msg sent by a Relayer to Chain A to close a channel with Chain B.

| Field        | Type                           | Label | Description |
| ------------ | ------------------------------ | ----- | ----------- |
| `port_id`    | [string](value.md#string) |       |             |
| `channel_id` | [string](value.md#string) |       |             |
| `signer`     | [string](value.md#string) |       |             |

### MsgChannelCloseInitResponse

MsgChannelCloseInitResponse defines the Msg/ChannelCloseInit response type.

### MsgChannelOpenAck

MsgChannelOpenAck defines a msg sent by a Relayer to Chain A to acknowledge the change of channel state to TRYOPEN on Chain B.

| Field                     | Type                                                                 | Label | Description |
| ------------------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `port_id`                 | [string](value.md#string)                                       |       |             |
| `channel_id`              | [string](value.md#string)                                       |       |             |
| `counterparty_channel_id` | [string](value.md#string)                                       |       |             |
| `counterparty_version`    | [string](value.md#string)                                       |       |             |
| `proof_try`               | [bytes](value.md#bytes)                                         |       |             |
| `proof_height`            | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |             |
| `signer`                  | [string](value.md#string)                                       |       |             |

### MsgChannelOpenAckResponse

MsgChannelOpenAckResponse defines the Msg/ChannelOpenAck response type.

### MsgChannelOpenConfirm

MsgChannelOpenConfirm defines a msg sent by a Relayer to Chain B to acknowledge the change of channel state to OPEN on Chain A.

| Field          | Type                                                                 | Label | Description |
| -------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `port_id`      | [string](value.md#string)                                       |       |             |
| `channel_id`   | [string](value.md#string)                                       |       |             |
| `proof_ack`    | [bytes](value.md#bytes)                                         |       |             |
| `proof_height` | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |             |
| `signer`       | [string](value.md#string)                                       |       |             |

### MsgChannelOpenConfirmResponse

MsgChannelOpenConfirmResponse defines the Msg/ChannelOpenConfirm response type.

### MsgChannelOpenInit

MsgChannelOpenInit defines an sdk.Msg to initialize a channel handshake. It is called by a relayer on Chain A.

| Field     | Type                                                 | Label | Description |
| --------- | ---------------------------------------------------- | ----- | ----------- |
| `port_id` | [string](value.md#string)                       |       |             |
| `channel` | [Channel](ibc.md#ibc.core.channel.v1.Channel) |       |             |
| `signer`  | [string](value.md#string)                       |       |             |

### MsgChannelOpenInitResponse

MsgChannelOpenInitResponse defines the Msg/ChannelOpenInit response type.

### MsgChannelOpenTry

MsgChannelOpenInit defines a msg sent by a Relayer to try to open a channel on Chain B.

| Field                  | Type                                                                 | Label | Description                                                                                                                           |
| ---------------------- | -------------------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `port_id`              | [string](value.md#string)                                       |       |                                                                                                                                       |
| `previous_channel_id`  | [string](value.md#string)                                       |       | in the case of crossing hello's, when both chains call OpenInit, we need the channel identifier of the previous channel in state INIT |
| `channel`              | [Channel](ibc.md#ibc.core.channel.v1.Channel)                 |       |                                                                                                                                       |
| `counterparty_version` | [string](value.md#string)                                       |       |                                                                                                                                       |
| `proof_init`           | [bytes](value.md#bytes)                                         |       |                                                                                                                                       |
| `proof_height`         | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |                                                                                                                                       |
| `signer`               | [string](value.md#string)                                       |       |                                                                                                                                       |

### MsgChannelOpenTryResponse

MsgChannelOpenTryResponse defines the Msg/ChannelOpenTry response type.

### MsgRecvPacket

MsgRecvPacket receives incoming IBC packet

| Field              | Type                                                                 | Label | Description |
| ------------------ | -------------------------------------------------------------------- | ----- | ----------- |
| `packet`           | [Packet](ibc.md#ibc.core.channel.v1.Packet)                   |       |             |
| `proof_commitment` | [bytes](value.md#bytes)                                         |       |             |
| `proof_height`     | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |             |
| `signer`           | [string](value.md#string)                                       |       |             |

### MsgRecvPacketResponse

MsgRecvPacketResponse defines the Msg/RecvPacket response type.

### MsgTimeout

MsgTimeout receives timed-out packet

| Field                | Type                                                                 | Label | Description |
| -------------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `packet`             | [Packet](ibc.md#ibc.core.channel.v1.Packet)                   |       |             |
| `proof_unreceived`   | [bytes](value.md#bytes)                                         |       |             |
| `proof_height`       | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |             |
| `next_sequence_recv` | [uint64](value.md#uint64)                                       |       |             |
| `signer`             | [string](value.md#string)                                       |       |             |

### MsgTimeoutOnClose

MsgTimeoutOnClose timed-out packet upon counterparty channel closure.

| Field                | Type                                                                 | Label | Description |
| -------------------- | -------------------------------------------------------------------- | ----- | ----------- |
| `packet`             | [Packet](ibc.md#ibc.core.channel.v1.Packet)                   |       |             |
| `proof_unreceived`   | [bytes](value.md#bytes)                                         |       |             |
| `proof_close`        | [bytes](value.md#bytes)                                         |       |             |
| `proof_height`       | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |             |
| `next_sequence_recv` | [uint64](value.md#uint64)                                       |       |             |
| `signer`             | [string](value.md#string)                                       |       |             |

### MsgTimeoutOnCloseResponse

MsgTimeoutOnCloseResponse defines the Msg/TimeoutOnClose response type.

### MsgTimeoutResponse

MsgTimeoutResponse defines the Msg/Timeout response type.

### Msg

Msg defines the ibc/channel Msg service.

| Method Name           | Request Type                                                                       | Response Type                                                                                      | Description                                                                  | HTTP Verb | Endpoint |
| --------------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | --------- | -------- |
| `ChannelOpenInit`     | [MsgChannelOpenInit](ibc.md#ibc.core.channel.v1.MsgChannelOpenInit)         | [MsgChannelOpenInitResponse](ibc.md#ibc.core.channel.v1.MsgChannelOpenInitResponse)         | ChannelOpenInit defines a rpc handler method for MsgChannelOpenInit.         |           |          |
| `ChannelOpenTry`      | [MsgChannelOpenTry](ibc.md#ibc.core.channel.v1.MsgChannelOpenTry)           | [MsgChannelOpenTryResponse](ibc.md#ibc.core.channel.v1.MsgChannelOpenTryResponse)           | ChannelOpenTry defines a rpc handler method for MsgChannelOpenTry.           |           |          |
| `ChannelOpenAck`      | [MsgChannelOpenAck](ibc.md#ibc.core.channel.v1.MsgChannelOpenAck)           | [MsgChannelOpenAckResponse](ibc.md#ibc.core.channel.v1.MsgChannelOpenAckResponse)           | ChannelOpenAck defines a rpc handler method for MsgChannelOpenAck.           |           |          |
| `ChannelOpenConfirm`  | [MsgChannelOpenConfirm](ibc.md#ibc.core.channel.v1.MsgChannelOpenConfirm)   | [MsgChannelOpenConfirmResponse](ibc.md#ibc.core.channel.v1.MsgChannelOpenConfirmResponse)   | ChannelOpenConfirm defines a rpc handler method for MsgChannelOpenConfirm.   |           |          |
| `ChannelCloseInit`    | [MsgChannelCloseInit](ibc.md#ibc.core.channel.v1.MsgChannelCloseInit)       | [MsgChannelCloseInitResponse](ibc.md#ibc.core.channel.v1.MsgChannelCloseInitResponse)       | ChannelCloseInit defines a rpc handler method for MsgChannelCloseInit.       |           |          |
| `ChannelCloseConfirm` | [MsgChannelCloseConfirm](ibc.md#ibc.core.channel.v1.MsgChannelCloseConfirm) | [MsgChannelCloseConfirmResponse](ibc.md#ibc.core.channel.v1.MsgChannelCloseConfirmResponse) | ChannelCloseConfirm defines a rpc handler method for MsgChannelCloseConfirm. |           |          |
| `RecvPacket`          | [MsgRecvPacket](ibc.md#ibc.core.channel.v1.MsgRecvPacket)                   | [MsgRecvPacketResponse](ibc.md#ibc.core.channel.v1.MsgRecvPacketResponse)                   | RecvPacket defines a rpc handler method for MsgRecvPacket.                   |           |          |
| `Timeout`             | [MsgTimeout](ibc.md#ibc.core.channel.v1.MsgTimeout)                         | [MsgTimeoutResponse](ibc.md#ibc.core.channel.v1.MsgTimeoutResponse)                         | Timeout defines a rpc handler method for MsgTimeout.                         |           |          |
| `TimeoutOnClose`      | [MsgTimeoutOnClose](ibc.md#ibc.core.channel.v1.MsgTimeoutOnClose)           | [MsgTimeoutOnCloseResponse](ibc.md#ibc.core.channel.v1.MsgTimeoutOnCloseResponse)           | TimeoutOnClose defines a rpc handler method for MsgTimeoutOnClose.           |           |          |
| `Acknowledgement`     | [MsgAcknowledgement](ibc.md#ibc.core.channel.v1.MsgAcknowledgement)         | [MsgAcknowledgementResponse](ibc.md#ibc.core.channel.v1.MsgAcknowledgementResponse)         | Acknowledgement defines a rpc handler method for MsgAcknowledgement.         |           |          |



## ibc/core/client/v1/genesis.proto

### GenesisMetadata

GenesisMetadata defines the genesis type for metadata that clients may return with ExportMetadata

| Field   | Type                         | Label | Description                                   |
| ------- | ---------------------------- | ----- | --------------------------------------------- |
| `key`   | [bytes](value.md#bytes) |       | store key of metadata without clientID-prefix |
| `value` | [bytes](value.md#bytes) |       | metadata value                                |

### GenesisState

GenesisState defines the ibc client submodule's genesis state.

| Field                  | Type                                                                                    | Label    | Description                                           |
| ---------------------- | --------------------------------------------------------------------------------------- | -------- | ----------------------------------------------------- |
| `clients`              | [IdentifiedClientState](ibc.md#ibc.core.client.v1.IdentifiedClientState)         | repeated | client states with their corresponding identifiers    |
| `clients_consensus`    | [ClientConsensusStates](ibc.md#ibc.core.client.v1.ClientConsensusStates)         | repeated | consensus states from each client                     |
| `clients_metadata`     | [IdentifiedGenesisMetadata](ibc.md#ibc.core.client.v1.IdentifiedGenesisMetadata) | repeated | metadata from each client                             |
| `params`               | [Params](ibc.md#ibc.core.client.v1.Params)                                       |          |                                                       |
| `create_localhost`     | [bool](value.md#bool)                                                              |          | create localhost on initialization                    |
| `next_client_sequence` | [uint64](value.md#uint64)                                                          |          | the sequence for the next generated client identifier |

### IdentifiedGenesisMetadata

IdentifiedGenesisMetadata has the client metadata with the corresponding client id.

| Field             | Type                                                                | Label    | Description |
| ----------------- | ------------------------------------------------------------------- | -------- | ----------- |
| `client_id`       | [string](value.md#string)                                      |          |             |
| `client_metadata` | [GenesisMetadata](ibc.md#ibc.core.client.v1.GenesisMetadata) | repeated |             |



## ibc/core/client/v1/query.proto

### QueryClientParamsRequest

QueryClientParamsRequest is the request type for the Query/ClientParams RPC method.

### QueryClientParamsResponse

QueryClientParamsResponse is the response type for the Query/ClientParams RPC method.

| Field    | Type                                              | Label | Description                                  |
| -------- | ------------------------------------------------- | ----- | -------------------------------------------- |
| `params` | [Params](ibc.md#ibc.core.client.v1.Params) |       | params defines the parameters of the module. |

### QueryClientStateRequest

QueryClientStateRequest is the request type for the Query/ClientState RPC method

| Field       | Type                           | Label | Description                    |
| ----------- | ------------------------------ | ----- | ------------------------------ |
| `client_id` | [string](value.md#string) |       | client state unique identifier |

### QueryClientStateResponse

QueryClientStateResponse is the response type for the Query/ClientState RPC method. Besides the client state, it includes a proof and the height from which the proof was retrieved.

| Field          | Type                                                     | Label | Description                                         |
| -------------- | -------------------------------------------------------- | ----- | --------------------------------------------------- |
| `client_state` | google.protobuf.Any |       | client state associated with the request identifier |
| `proof`        | [bytes](value.md#bytes)                             |       | merkle proof of existence                           |
| `proof_height` | [Height](ibc.md#ibc.core.client.v1.Height)        |       | height at which the proof was retrieved             |

### QueryClientStatesRequest

QueryClientStatesRequest is the request type for the Query/ClientStates RPC method

| Field        | Type                                                                                         | Label | Description        |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ------------------ |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination request |

### QueryClientStatesResponse

QueryClientStatesResponse is the response type for the Query/ClientStates RPC method.

| Field           | Type                                                                                           | Label    | Description                               |
| --------------- | ---------------------------------------------------------------------------------------------- | -------- | ----------------------------------------- |
| `client_states` | [IdentifiedClientState](ibc.md#ibc.core.client.v1.IdentifiedClientState)                | repeated | list of stored ClientStates of the chain. |
| `pagination`    | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination response                       |

### QueryConsensusStateRequest

QueryConsensusStateRequest is the request type for the Query/ConsensusState RPC method. Besides the consensus state, it includes a proof and the height from which the proof was retrieved.

| Field             | Type                           | Label | Description                                                                             |
| ----------------- | ------------------------------ | ----- | --------------------------------------------------------------------------------------- |
| `client_id`       | [string](value.md#string) |       | client identifier                                                                       |
| `revision_number` | [uint64](value.md#uint64) |       | consensus state revision number                                                         |
| `revision_height` | [uint64](value.md#uint64) |       | consensus state revision height                                                         |
| `latest_height`   | [bool](value.md#bool)     |       | latest_height overrrides the height field and queries the latest stored ConsensusState |

### QueryConsensusStateResponse

QueryConsensusStateResponse is the response type for the Query/ConsensusState RPC method

| Field             | Type                                                     | Label | Description                                                               |
| ----------------- | -------------------------------------------------------- | ----- | ------------------------------------------------------------------------- |
| `consensus_state` | google.protobuf.Any |       | consensus state associated with the client identifier at the given height |
| `proof`           | [bytes](value.md#bytes)                             |       | merkle proof of existence                                                 |
| `proof_height`    | [Height](ibc.md#ibc.core.client.v1.Height)        |       | height at which the proof was retrieved                                   |

### QueryConsensusStatesRequest

QueryConsensusStatesRequest is the request type for the Query/ConsensusStates RPC method.

| Field        | Type                                                                                         | Label | Description        |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ------------------ |
| `client_id`  | [string](value.md#string)                                                               |       | client identifier  |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination request |

### QueryConsensusStatesResponse

QueryConsensusStatesResponse is the response type for the Query/ConsensusStates RPC method

| Field              | Type                                                                                           | Label    | Description                                     |
| ------------------ | ---------------------------------------------------------------------------------------------- | -------- | ----------------------------------------------- |
| `consensus_states` | [ConsensusStateWithHeight](ibc.md#ibc.core.client.v1.ConsensusStateWithHeight)          | repeated | consensus states associated with the identifier |
| `pagination`       | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination response                             |

### Query

Query provides defines the gRPC querier service

| Method Name       | Request Type                                                                                | Response Type                                                                                 | Description                                                                                | HTTP Verb | Endpoint                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | --------- | ------------------------------------------------------------------------------------------------------------- |
| `ClientState`     | [QueryClientStateRequest](ibc.md#ibc.core.client.v1.QueryClientStateRequest)         | [QueryClientStateResponse](ibc.md#ibc.core.client.v1.QueryClientStateResponse)         | ClientState queries an IBC light client.                                                   | GET       | /ibc/core/client/v1beta1/client_states/{client_id}                                                          |
| `ClientStates`    | [QueryClientStatesRequest](ibc.md#ibc.core.client.v1.QueryClientStatesRequest)       | [QueryClientStatesResponse](ibc.md#ibc.core.client.v1.QueryClientStatesResponse)       | ClientStates queries all the IBC light clients of a chain.                                 | GET       | /ibc/core/client/v1beta1/client_states                                                                       |
| `ConsensusState`  | [QueryConsensusStateRequest](ibc.md#ibc.core.client.v1.QueryConsensusStateRequest)   | [QueryConsensusStateResponse](ibc.md#ibc.core.client.v1.QueryConsensusStateResponse)   | ConsensusState queries a consensus state associated with a client state at a given height. | GET       | /ibc/core/client/v1beta1/consensus_states/{client_id}/revision/{revision_number}/height/{revision_height} |
| `ConsensusStates` | [QueryConsensusStatesRequest](ibc.md#ibc.core.client.v1.QueryConsensusStatesRequest) | [QueryConsensusStatesResponse](ibc.md#ibc.core.client.v1.QueryConsensusStatesResponse) | ConsensusStates queries all the consensus state associated with a given client.            | GET       | /ibc/core/client/v1beta1/consensus_states/{client_id}                                                       |
| `ClientParams`    | [QueryClientParamsRequest](ibc.md#ibc.core.client.v1.QueryClientParamsRequest)       | [QueryClientParamsResponse](ibc.md#ibc.core.client.v1.QueryClientParamsResponse)       | ClientParams queries all parameters of the ibc client.                                     | GET       | /ibc/client/v1beta1/params                                                                                    |



## ibc/core/client/v1/tx.proto

### MsgCreateClient

MsgCreateClient defines a message to create an IBC client

| Field             | Type                                                     | Label | Description                                                                    |
| ----------------- | -------------------------------------------------------- | ----- | ------------------------------------------------------------------------------ |
| `client_state`    | google.protobuf.Any |       | light client state                                                             |
| `consensus_state` | google.protobuf.Any |       | consensus state associated with the client that corresponds to a given height. |
| `signer`          | [string](value.md#string)                           |       | signer address                                                                 |

### MsgCreateClientResponse

MsgCreateClientResponse defines the Msg/CreateClient response type.

### MsgSubmitMisbehaviour

MsgSubmitMisbehaviour defines an sdk.Msg type that submits Evidence for light client misbehaviour.

| Field          | Type                                                     | Label | Description                                     |
| -------------- | -------------------------------------------------------- | ----- | ----------------------------------------------- |
| `client_id`    | [string](value.md#string)                           |       | client unique identifier                        |
| `misbehaviour` | google.protobuf.Any |       | misbehaviour used for freezing the light client |
| `signer`       | [string](value.md#string)                           |       | signer address                                  |

### MsgSubmitMisbehaviourResponse

MsgSubmitMisbehaviourResponse defines the Msg/SubmitMisbehaviour response type.

### MsgUpdateClient

MsgUpdateClient defines an sdk.Msg to update a IBC client state using the given header.

| Field       | Type                                                     | Label | Description                       |
| ----------- | -------------------------------------------------------- | ----- | --------------------------------- |
| `client_id` | [string](value.md#string)                           |       | client unique identifier          |
| `header`    | google.protobuf.Any |       | header to update the light client |
| `signer`    | [string](value.md#string)                           |       | signer address                    |

### MsgUpdateClientResponse

MsgUpdateClientResponse defines the Msg/UpdateClient response type.

### MsgUpgradeClient

MsgUpgradeClient defines an sdk.Msg to upgrade an IBC client to a new client state

| Field                           | Type                                                     | Label | Description                                                                                             |
| ------------------------------- | -------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------------- |
| `client_id`                     | [string](value.md#string)                           |       | client unique identifier                                                                                |
| `client_state`                  | google.protobuf.Any |       | upgraded client state                                                                                   |
| `consensus_state`               | google.protobuf.Any |       | upgraded consensus state, only contains enough information to serve as a basis of trust in update logic |
| `proof_upgrade_client`          | [bytes](value.md#bytes)                             |       | proof that old chain committed to new client                                                            |
| `proof_upgrade_consensus_state` | [bytes](value.md#bytes)                             |       | proof that old chain committed to new consensus state                                                   |
| `signer`                        | [string](value.md#string)                           |       | signer address                                                                                          |

### MsgUpgradeClientResponse

MsgUpgradeClientResponse defines the Msg/UpgradeClient response type.

### Msg

Msg defines the ibc/client Msg service.

| Method Name          | Request Type                                                                    | Response Type                                                                                   | Description                                                                | HTTP Verb | Endpoint |
| -------------------- | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | --------- | -------- |
| `CreateClient`       | [MsgCreateClient](ibc.md#ibc.core.client.v1.MsgCreateClient)             | [MsgCreateClientResponse](ibc.md#ibc.core.client.v1.MsgCreateClientResponse)             | CreateClient defines a rpc handler method for MsgCreateClient.             |           |          |
| `UpdateClient`       | [MsgUpdateClient](ibc.md#ibc.core.client.v1.MsgUpdateClient)             | [MsgUpdateClientResponse](ibc.md#ibc.core.client.v1.MsgUpdateClientResponse)             | UpdateClient defines a rpc handler method for MsgUpdateClient.             |           |          |
| `UpgradeClient`      | [MsgUpgradeClient](ibc.md#ibc.core.client.v1.MsgUpgradeClient)           | [MsgUpgradeClientResponse](ibc.md#ibc.core.client.v1.MsgUpgradeClientResponse)           | UpgradeClient defines a rpc handler method for MsgUpgradeClient.           |           |          |
| `SubmitMisbehaviour` | [MsgSubmitMisbehaviour](ibc.md#ibc.core.client.v1.MsgSubmitMisbehaviour) | [MsgSubmitMisbehaviourResponse](ibc.md#ibc.core.client.v1.MsgSubmitMisbehaviourResponse) | SubmitMisbehaviour defines a rpc handler method for MsgSubmitMisbehaviour. |           |          |



## ibc/core/commitment/v1/commitment.proto

### MerklePath

MerklePath is the path used to verify commitment proofs, which can be an arbitrary structured object (defined by a commitment type). MerklePath is represented from root-to-leaf

| Field      | Type                           | Label    | Description |
| ---------- | ------------------------------ | -------- | ----------- |
| `key_path` | [string](value.md#string) | repeated |             |

### MerklePrefix

MerklePrefix is merkle path prefixed to the key. The constructed key from the Path and the key will be append(Path.KeyPath, append(Path.KeyPrefix, key...))

| Field        | Type                         | Label | Description |
| ------------ | ---------------------------- | ----- | ----------- |
| `key_prefix` | [bytes](value.md#bytes) |       |             |

### MerkleProof

MerkleProof is a wrapper type over a chain of CommitmentProofs. It demonstrates membership or non-membership for an element or set of elements, verifiable in conjunction with a known commitment root. Proofs should be succinct. MerkleProofs are ordered from leaf-to-root

| Field    | Type                                                         | Label    | Description |
| -------- | ------------------------------------------------------------ | -------- | ----------- |
| `proofs` | [ics23.CommitmentProof](#ics23.CommitmentProof) | repeated |             |

### MerkleRoot

MerkleRoot defines a merkle root hash. In the Cosmos SDK, the AppHash of a block header becomes the root.

| Field  | Type                         | Label | Description |
| ------ | ---------------------------- | ----- | ----------- |
| `hash` | [bytes](value.md#bytes) |       |             |



## ibc/core/connection/v1/connection.proto

### ClientPaths

ClientPaths define all the connection paths for a client state.

| Field   | Type                           | Label    | Description              |
| ------- | ------------------------------ | -------- | ------------------------ |
| `paths` | [string](value.md#string) | repeated | list of connection paths |

### ConnectionEnd

ConnectionEnd defines a stateful object on a chain connected to another separate one. NOTE: there must only be 2 defined ConnectionEnds to establish a connection between two chains.

| Field          | Type                                                              | Label    | Description                                                                                                                                            |
| -------------- | ----------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `client_id`    | [string](value.md#string)                                    |          | client associated with this connection.                                                                                                                |
| `versions`     | [Version](ibc.md#ibc.core.connection.v1.Version)           | repeated | IBC version which can be utilised to determine encodings or protocols for channels or packets utilising this connection.                               |
| `state`        | [State](ibc.md#ibc.core.connection.v1.State)               |          | current state of the connection end.                                                                                                                   |
| `counterparty` | [Counterparty](ibc.md#ibc.core.connection.v1.Counterparty) |          | counterparty chain associated with this connection.                                                                                                    |
| `delay_period` | [uint64](value.md#uint64)                                    |          | delay period that must pass before a consensus state can be used for packet-verification NOTE: delay period logic is only implemented by some clients. |

### ConnectionPaths

ConnectionPaths define all the connection paths for a given client state.

| Field       | Type                           | Label    | Description                    |
| ----------- | ------------------------------ | -------- | ------------------------------ |
| `client_id` | [string](value.md#string) |          | client state unique identifier |
| `paths`     | [string](value.md#string) | repeated | list of connection paths       |

### Counterparty

Counterparty defines the counterparty chain associated with a connection end.

| Field           | Type                                                                                     | Label | Description                                                                                 |
| --------------- | ---------------------------------------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------- |
| `client_id`     | [string](value.md#string)                                                           |       | identifies the client on the counterparty chain associated with a given connection.         |
| `connection_id` | [string](value.md#string)                                                           |       | identifies the connection end on the counterparty chain associated with a given connection. |
| `prefix`        | [ibc.core.commitment.v1.MerklePrefix](ibc.md#ibc.core.commitment.v1.MerklePrefix) |       | commitment merkle prefix of the counterparty chain.                                         |

### IdentifiedConnection

IdentifiedConnection defines a connection with additional connection identifier field.

| Field          | Type                                                              | Label    | Description                                                                                                             |
| -------------- | ----------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------- |
| `id`           | [string](value.md#string)                                    |          | connection identifier.                                                                                                  |
| `client_id`    | [string](value.md#string)                                    |          | client associated with this connection.                                                                                 |
| `versions`     | [Version](ibc.md#ibc.core.connection.v1.Version)           | repeated | IBC version which can be utilised to determine encodings or protocols for channels or packets utilising this connection |
| `state`        | [State](ibc.md#ibc.core.connection.v1.State)               |          | current state of the connection end.                                                                                    |
| `counterparty` | [Counterparty](ibc.md#ibc.core.connection.v1.Counterparty) |          | counterparty chain associated with this connection.                                                                     |
| `delay_period` | [uint64](value.md#uint64)                                    |          | delay period associated with this connection.                                                                           |

### Version

Version defines the versioning scheme used to negotiate the IBC verison in the connection handshake.

| Field        | Type                           | Label    | Description                                               |
| ------------ | ------------------------------ | -------- | --------------------------------------------------------- |
| `identifier` | [string](value.md#string) |          | unique version identifier                                 |
| `features`   | [string](value.md#string) | repeated | list of features compatible with the specified identifier |

### State

State defines if a connection is in one of the following states: INIT, TRYOPEN, OPEN or UNINITIALIZED.

| Name                              | Number | Description                                                                     |
| --------------------------------- | ------ | ------------------------------------------------------------------------------- |
| STATE_UNINITIALIZED_UNSPECIFIED | 0      | Default State                                                                   |
| STATE_INIT                       | 1      | A connection end has just started the opening handshake.                        |
| STATE_TRYOPEN                    | 2      | A connection end has acknowledged the handshake step on the counterparty chain. |
| STATE_OPEN                       | 3      | A connection end has completed the handshake.                                   |



## ibc/core/connection/v1/genesis.proto

### GenesisState

GenesisState defines the ibc connection submodule's genesis state.

| Field                      | Type                                                                              | Label    | Description                                               |
| -------------------------- | --------------------------------------------------------------------------------- | -------- | --------------------------------------------------------- |
| `connections`              | [IdentifiedConnection](ibc.md#ibc.core.connection.v1.IdentifiedConnection) | repeated |                                                           |
| `client_connection_paths`  | [ConnectionPaths](ibc.md#ibc.core.connection.v1.ConnectionPaths)           | repeated |                                                           |
| `next_connection_sequence` | [uint64](value.md#uint64)                                                    |          | the sequence for the next generated connection identifier |



## ibc/core/connection/v1/query.proto

### QueryClientConnectionsRequest

QueryClientConnectionsRequest is the request type for the Query/ClientConnections RPC method

| Field       | Type                           | Label | Description                                    |
| ----------- | ------------------------------ | ----- | ---------------------------------------------- |
| `client_id` | [string](value.md#string) |       | client identifier associated with a connection |

### QueryClientConnectionsResponse

QueryClientConnectionsResponse is the response type for the Query/ClientConnections RPC method

| Field              | Type                                                                 | Label    | Description                                                 |
| ------------------ | -------------------------------------------------------------------- | -------- | ----------------------------------------------------------- |
| `connection_paths` | [string](value.md#string)                                       | repeated | slice of all the connection paths associated with a client. |
| `proof`            | [bytes](value.md#bytes)                                         |          | merkle proof of existence                                   |
| `proof_height`     | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |          | height at which the proof was generated                     |

### QueryConnectionClientStateRequest

QueryConnectionClientStateRequest is the request type for the Query/ConnectionClientState RPC method

| Field           | Type                           | Label | Description           |
| --------------- | ------------------------------ | ----- | --------------------- |
| `connection_id` | [string](value.md#string) |       | connection identifier |

### QueryConnectionClientStateResponse

QueryConnectionClientStateResponse is the response type for the Query/ConnectionClientState RPC method

| Field                     | Type                                                                                               | Label | Description                              |
| ------------------------- | -------------------------------------------------------------------------------------------------- | ----- | ---------------------------------------- |
| `identified_client_state` | [ibc.core.client.v1.IdentifiedClientState](ibc.md#ibc.core.client.v1.IdentifiedClientState) |       | client state associated with the channel |
| `proof`                   | [bytes](value.md#bytes)                                                                       |       | merkle proof of existence                |
| `proof_height`            | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)                               |       | height at which the proof was retrieved  |

### QueryConnectionConsensusStateRequest

QueryConnectionConsensusStateRequest is the request type for the Query/ConnectionConsensusState RPC method

| Field             | Type                           | Label | Description           |
| ----------------- | ------------------------------ | ----- | --------------------- |
| `connection_id`   | [string](value.md#string) |       | connection identifier |
| `revision_number` | [uint64](value.md#uint64) |       |                       |
| `revision_height` | [uint64](value.md#uint64) |       |                       |

### QueryConnectionConsensusStateResponse

QueryConnectionConsensusStateResponse is the response type for the Query/ConnectionConsensusState RPC method

| Field             | Type                                                                 | Label | Description                                   |
| ----------------- | -------------------------------------------------------------------- | ----- | --------------------------------------------- |
| `consensus_state` | google.protobuf.Any             |       | consensus state associated with the channel   |
| `client_id`       | [string](value.md#string)                                       |       | client ID associated with the consensus state |
| `proof`           | [bytes](value.md#bytes)                                         |       | merkle proof of existence                     |
| `proof_height`    | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved       |

### QueryConnectionRequest

QueryConnectionRequest is the request type for the Query/Connection RPC method

| Field           | Type                           | Label | Description                  |
| --------------- | ------------------------------ | ----- | ---------------------------- |
| `connection_id` | [string](value.md#string) |       | connection unique identifier |

### QueryConnectionResponse

QueryConnectionResponse is the response type for the Query/Connection RPC method. Besides the connection end, it includes a proof and the height from which the proof was retrieved.

| Field          | Type                                                                 | Label | Description                                       |
| -------------- | -------------------------------------------------------------------- | ----- | ------------------------------------------------- |
| `connection`   | [ConnectionEnd](ibc.md#ibc.core.connection.v1.ConnectionEnd)  |       | connection associated with the request identifier |
| `proof`        | [bytes](value.md#bytes)                                         |       | merkle proof of existence                         |
| `proof_height` | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | height at which the proof was retrieved           |

### QueryConnectionsRequest

QueryConnectionsRequest is the request type for the Query/Connections RPC method

| Field        | Type                                                                                         | Label | Description |
| ------------ | -------------------------------------------------------------------------------------------- | ----- | ----------- |
| `pagination` | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       |             |

### QueryConnectionsResponse

QueryConnectionsResponse is the response type for the Query/Connections RPC method.

| Field         | Type                                                                                           | Label    | Description                              |
| ------------- | ---------------------------------------------------------------------------------------------- | -------- | ---------------------------------------- |
| `connections` | [IdentifiedConnection](ibc.md#ibc.core.connection.v1.IdentifiedConnection)              | repeated | list of stored connections of the chain. |
| `pagination`  | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination response                      |
| `height`      | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)                           |          | query block height                       |

### Query

Query provides defines the gRPC querier service

| Method Name                | Request Type                                                                                                      | Response Type                                                                                                       | Description                                                                          | HTTP Verb | Endpoint                                                                                                                         |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `Connection`               | [QueryConnectionRequest](ibc.md#ibc.core.connection.v1.QueryConnectionRequest)                             | [QueryConnectionResponse](ibc.md#ibc.core.connection.v1.QueryConnectionResponse)                             | Connection queries an IBC connection end.                                            | GET       | /ibc/core/connection/v1beta1/connections/{connection_id}                                                                        |
| `Connections`              | [QueryConnectionsRequest](ibc.md#ibc.core.connection.v1.QueryConnectionsRequest)                           | [QueryConnectionsResponse](ibc.md#ibc.core.connection.v1.QueryConnectionsResponse)                           | Connections queries all the IBC connections of a chain.                              | GET       | /ibc/core/connection/v1beta1/connections                                                                                         |
| `ClientConnections`        | [QueryClientConnectionsRequest](ibc.md#ibc.core.connection.v1.QueryClientConnectionsRequest)               | [QueryClientConnectionsResponse](ibc.md#ibc.core.connection.v1.QueryClientConnectionsResponse)               | ClientConnections queries the connection paths associated with a client state.       | GET       | /ibc/core/connection/v1beta1/client_connections/{client_id}                                                                    |
| `ConnectionClientState`    | [QueryConnectionClientStateRequest](ibc.md#ibc.core.connection.v1.QueryConnectionClientStateRequest)       | [QueryConnectionClientStateResponse](ibc.md#ibc.core.connection.v1.QueryConnectionClientStateResponse)       | ConnectionClientState queries the client state associated with the connection.       | GET       | /ibc/core/connection/v1beta1/connections/{connection_id}/client_state                                                          |
| `ConnectionConsensusState` | [QueryConnectionConsensusStateRequest](ibc.md#ibc.core.connection.v1.QueryConnectionConsensusStateRequest) | [QueryConnectionConsensusStateResponse](ibc.md#ibc.core.connection.v1.QueryConnectionConsensusStateResponse) | ConnectionConsensusState queries the consensus state associated with the connection. | GET       | /ibc/core/connection/v1beta1/connections/{connection_id}/consensus_state/revision/{revision_number}/height/{revision_height} |



## ibc/core/connection/v1/tx.proto

### MsgConnectionOpenAck

MsgConnectionOpenAck defines a msg sent by a Relayer to Chain A to acknowledge the change of connection state to TRYOPEN on Chain B.

| Field                        | Type                                                                 | Label | Description                                                                     |
| ---------------------------- | -------------------------------------------------------------------- | ----- | ------------------------------------------------------------------------------- |
| `connection_id`              | [string](value.md#string)                                       |       |                                                                                 |
| `counterparty_connection_id` | [string](value.md#string)                                       |       |                                                                                 |
| `version`                    | [Version](ibc.md#ibc.core.connection.v1.Version)              |       |                                                                                 |
| `client_state`               | google.protobuf.Any             |       |                                                                                 |
| `proof_height`               | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |                                                                                 |
| `proof_try`                  | [bytes](value.md#bytes)                                         |       | proof of the initialization the connection on Chain B: `UNITIALIZED -> TRYOPEN` |
| `proof_client`               | [bytes](value.md#bytes)                                         |       | proof of client state included in message                                       |
| `proof_consensus`            | [bytes](value.md#bytes)                                         |       | proof of client consensus state                                                 |
| `consensus_height`           | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |                                                                                 |
| `signer`                     | [string](value.md#string)                                       |       |                                                                                 |

### MsgConnectionOpenAckResponse

MsgConnectionOpenAckResponse defines the Msg/ConnectionOpenAck response type.

### MsgConnectionOpenConfirm

MsgConnectionOpenConfirm defines a msg sent by a Relayer to Chain B to acknowledge the change of connection state to OPEN on Chain A.

| Field           | Type                                                                 | Label | Description                                                             |
| --------------- | -------------------------------------------------------------------- | ----- | ----------------------------------------------------------------------- |
| `connection_id` | [string](value.md#string)                                       |       |                                                                         |
| `proof_ack`     | [bytes](value.md#bytes)                                         |       | proof for the change of the connection state on Chain A: `INIT -> OPEN` |
| `proof_height`  | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       |                                                                         |
| `signer`        | [string](value.md#string)                                       |       |                                                                         |

### MsgConnectionOpenConfirmResponse

MsgConnectionOpenConfirmResponse defines the Msg/ConnectionOpenConfirm response type.

### MsgConnectionOpenInit

MsgConnectionOpenInit defines the msg sent by an account on Chain A to initialize a connection with Chain B.

| Field          | Type                                                              | Label | Description |
| -------------- | ----------------------------------------------------------------- | ----- | ----------- |
| `client_id`    | [string](value.md#string)                                    |       |             |
| `counterparty` | [Counterparty](ibc.md#ibc.core.connection.v1.Counterparty) |       |             |
| `version`      | [Version](ibc.md#ibc.core.connection.v1.Version)           |       |             |
| `delay_period` | [uint64](value.md#uint64)                                    |       |             |
| `signer`       | [string](value.md#string)                                    |       |             |

### MsgConnectionOpenInitResponse

MsgConnectionOpenInitResponse defines the Msg/ConnectionOpenInit response type.

### MsgConnectionOpenTry

MsgConnectionOpenTry defines a msg sent by a Relayer to try to open a connection on Chain B.

| Field                    | Type                                                                 | Label    | Description                                                                                                                                 |
| ------------------------ | -------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `client_id`              | [string](value.md#string)                                       |          |                                                                                                                                             |
| `previous_connection_id` | [string](value.md#string)                                       |          | in the case of crossing hello's, when both chains call OpenInit, we need the connection identifier of the previous connection in state INIT |
| `client_state`           | google.protobuf.Any             |          |                                                                                                                                             |
| `counterparty`           | [Counterparty](ibc.md#ibc.core.connection.v1.Counterparty)    |          |                                                                                                                                             |
| `delay_period`           | [uint64](value.md#uint64)                                       |          |                                                                                                                                             |
| `counterparty_versions`  | [Version](ibc.md#ibc.core.connection.v1.Version)              | repeated |                                                                                                                                             |
| `proof_height`           | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |          |                                                                                                                                             |
| `proof_init`             | [bytes](value.md#bytes)                                         |          | proof of the initialization the connection on Chain A: `UNITIALIZED -> INIT`                                                                |
| `proof_client`           | [bytes](value.md#bytes)                                         |          | proof of client state included in message                                                                                                   |
| `proof_consensus`        | [bytes](value.md#bytes)                                         |          | proof of client consensus state                                                                                                             |
| `consensus_height`       | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |          |                                                                                                                                             |
| `signer`                 | [string](value.md#string)                                       |          |                                                                                                                                             |

### MsgConnectionOpenTryResponse

MsgConnectionOpenTryResponse defines the Msg/ConnectionOpenTry response type.

### Msg

Msg defines the ibc/connection Msg service.

| Method Name             | Request Type                                                                              | Response Type                                                                                             | Description                                                                      | HTTP Verb | Endpoint |
| ----------------------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | --------- | -------- |
| `ConnectionOpenInit`    | [MsgConnectionOpenInit](ibc.md#ibc.core.connection.v1.MsgConnectionOpenInit)       | [MsgConnectionOpenInitResponse](ibc.md#ibc.core.connection.v1.MsgConnectionOpenInitResponse)       | ConnectionOpenInit defines a rpc handler method for MsgConnectionOpenInit.       |           |          |
| `ConnectionOpenTry`     | [MsgConnectionOpenTry](ibc.md#ibc.core.connection.v1.MsgConnectionOpenTry)         | [MsgConnectionOpenTryResponse](ibc.md#ibc.core.connection.v1.MsgConnectionOpenTryResponse)         | ConnectionOpenTry defines a rpc handler method for MsgConnectionOpenTry.         |           |          |
| `ConnectionOpenAck`     | [MsgConnectionOpenAck](ibc.md#ibc.core.connection.v1.MsgConnectionOpenAck)         | [MsgConnectionOpenAckResponse](ibc.md#ibc.core.connection.v1.MsgConnectionOpenAckResponse)         | ConnectionOpenAck defines a rpc handler method for MsgConnectionOpenAck.         |           |          |
| `ConnectionOpenConfirm` | [MsgConnectionOpenConfirm](ibc.md#ibc.core.connection.v1.MsgConnectionOpenConfirm) | [MsgConnectionOpenConfirmResponse](ibc.md#ibc.core.connection.v1.MsgConnectionOpenConfirmResponse) | ConnectionOpenConfirm defines a rpc handler method for MsgConnectionOpenConfirm. |           |          |



## ibc/core/types/v1/genesis.proto

### GenesisState

GenesisState defines the ibc module's genesis state.

| Field                | Type                                                                                     | Label | Description                        |
| -------------------- | ---------------------------------------------------------------------------------------- | ----- | ---------------------------------- |
| `client_genesis`     | [ibc.core.client.v1.GenesisState](ibc.md#ibc.core.client.v1.GenesisState)         |       | ICS002 - Clients genesis state     |
| `connection_genesis` | [ibc.core.connection.v1.GenesisState](ibc.md#ibc.core.connection.v1.GenesisState) |       | ICS003 - Connections genesis state |
| `channel_genesis`    | [ibc.core.channel.v1.GenesisState](ibc.md#ibc.core.channel.v1.GenesisState)       |       | ICS004 - Channel genesis state     |



## ibc/lightclients/localhost/v1/localhost.proto

### ClientState

ClientState defines a loopback (localhost) client. It requires (read-only) access to keys outside the client prefix.

| Field      | Type                                                                 | Label | Description              |
| ---------- | -------------------------------------------------------------------- | ----- | ------------------------ |
| `chain_id` | [string](value.md#string)                                       |       | self chain ID            |
| `height`   | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |       | self latest block height |



## ibc/lightclients/solomachine/v1/solomachine.proto

### ChannelStateData

ChannelStateData returns the SignBytes data for channel state verification.

| Field     | Type                                                                     | Label | Description |
| --------- | ------------------------------------------------------------------------ | ----- | ----------- |
| `path`    | [bytes](value.md#bytes)                                             |       |             |
| `channel` | [ibc.core.channel.v1.Channel](ibc.md#ibc.core.channel.v1.Channel) |       |             |

### ClientState

ClientState defines a solo machine client that tracks the current consensus state and if the client is frozen.

| Field                         | Type                                                                           | Label | Description                                                                                                           |
| ----------------------------- | ------------------------------------------------------------------------------ | ----- | --------------------------------------------------------------------------------------------------------------------- |
| `sequence`                    | [uint64](value.md#uint64)                                                 |       | latest sequence of the client state                                                                                   |
| `frozen_sequence`             | [uint64](value.md#uint64)                                                 |       | frozen sequence of the solo machine                                                                                   |
| `consensus_state`             | [ConsensusState](ibc.md#ibc.lightclients.solomachine.v1.ConsensusState) |       |                                                                                                                       |
| `allow_update_after_proposal` | [bool](value.md#bool)                                                     |       | when set to true, will allow governance to update a solo machine client. The client will be unfrozen if it is frozen. |

### ClientStateData

ClientStateData returns the SignBytes data for client state verification.

| Field          | Type                                                     | Label | Description |
| -------------- | -------------------------------------------------------- | ----- | ----------- |
| `path`         | [bytes](value.md#bytes)                             |       |             |
| `client_state` | google.protobuf.Any |       |             |

### ConnectionStateData

ConnectionStateData returns the SignBytes data for connection state verification.

| Field        | Type                                                                                       | Label | Description |
| ------------ | ------------------------------------------------------------------------------------------ | ----- | ----------- |
| `path`       | [bytes](value.md#bytes)                                                               |       |             |
| `connection` | [ibc.core.connection.v1.ConnectionEnd](ibc.md#ibc.core.connection.v1.ConnectionEnd) |       |             |

### ConsensusState

ConsensusState defines a solo machine consensus state. The sequence of a consensus state is contained in the "height" key used in storing the consensus state.

| Field         | Type                                                     | Label | Description                                                                                                                                                         |
| ------------- | -------------------------------------------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `public_key`  | google.protobuf.Any |       | public key of the solo machine                                                                                                                                      |
| `diversifier` | [string](value.md#string)                           |       | diversifier allows the same public key to be re-used across different solo machine clients (potentially on different chains) without being considered misbehaviour. |
| `timestamp`   | [uint64](value.md#uint64)                           |       |                                                                                                                                                                     |

### ConsensusStateData

ConsensusStateData returns the SignBytes data for consensus state verification.

| Field             | Type                                                     | Label | Description |
| ----------------- | -------------------------------------------------------- | ----- | ----------- |
| `path`            | [bytes](value.md#bytes)                             |       |             |
| `consensus_state` | google.protobuf.Any |       |             |

### Header

Header defines a solo machine consensus header

| Field             | Type                                                     | Label | Description                                   |
| ----------------- | -------------------------------------------------------- | ----- | --------------------------------------------- |
| `sequence`        | [uint64](value.md#uint64)                           |       | sequence to update solo machine public key at |
| `timestamp`       | [uint64](value.md#uint64)                           |       |                                               |
| `signature`       | [bytes](value.md#bytes)                             |       |                                               |
| `new_public_key`  | google.protobuf.Any |       |                                               |
| `new_diversifier` | [string](value.md#string)                           |       |                                               |

### HeaderData

HeaderData returns the SignBytes data for update verification.

| Field             | Type                                                     | Label | Description        |
| ----------------- | -------------------------------------------------------- | ----- | ------------------ |
| `new_pub_key`     | google.protobuf.Any |       | header public key  |
| `new_diversifier` | [string](value.md#string)                           |       | header diversifier |

### Misbehaviour

Misbehaviour defines misbehaviour for a solo machine which consists of a sequence and two signatures over different messages at that sequence.

| Field           | Type                                                                               | Label | Description |
| --------------- | ---------------------------------------------------------------------------------- | ----- | ----------- |
| `client_id`     | [string](value.md#string)                                                     |       |             |
| `sequence`      | [uint64](value.md#uint64)                                                     |       |             |
| `signature_one` | [SignatureAndData](ibc.md#ibc.lightclients.solomachine.v1.SignatureAndData) |       |             |
| `signature_two` | [SignatureAndData](ibc.md#ibc.lightclients.solomachine.v1.SignatureAndData) |       |             |

### NextSequenceRecvData

NextSequenceRecvData returns the SignBytes data for verification of the next sequence to be received.

| Field           | Type                           | Label | Description |
| --------------- | ------------------------------ | ----- | ----------- |
| `path`          | [bytes](value.md#bytes)   |       |             |
| `next_seq_recv` | [uint64](value.md#uint64) |       |             |

### PacketAcknowledgementData

PacketAcknowledgementData returns the SignBytes data for acknowledgement verification.

| Field             | Type                         | Label | Description |
| ----------------- | ---------------------------- | ----- | ----------- |
| `path`            | [bytes](value.md#bytes) |       |             |
| `acknowledgement` | [bytes](value.md#bytes) |       |             |

### PacketCommitmentData

PacketCommitmentData returns the SignBytes data for packet commitment verification.

| Field        | Type                         | Label | Description |
| ------------ | ---------------------------- | ----- | ----------- |
| `path`       | [bytes](value.md#bytes) |       |             |
| `commitment` | [bytes](value.md#bytes) |       |             |

### PacketReceiptAbsenceData

PacketReceiptAbsenceData returns the SignBytes data for packet receipt absence verification.

| Field  | Type                         | Label | Description |
| ------ | ---------------------------- | ----- | ----------- |
| `path` | [bytes](value.md#bytes) |       |             |

### SignBytes

SignBytes defines the signed bytes used for signature verification.

| Field         | Type                                                               | Label | Description           |
| ------------- | ------------------------------------------------------------------ | ----- | --------------------- |
| `sequence`    | [uint64](value.md#uint64)                                     |       |                       |
| `timestamp`   | [uint64](value.md#uint64)                                     |       |                       |
| `diversifier` | [string](value.md#string)                                     |       |                       |
| `data_type`   | [DataType](ibc.md#ibc.lightclients.solomachine.v1.DataType) |       | type of the data used |
| `data`        | [bytes](value.md#bytes)                                       |       | marshaled data        |

### SignatureAndData

SignatureAndData contains a signature and the data signed over to create that signature.

| Field       | Type                                                               | Label | Description |
| ----------- | ------------------------------------------------------------------ | ----- | ----------- |
| `signature` | [bytes](value.md#bytes)                                       |       |             |
| `data_type` | [DataType](ibc.md#ibc.lightclients.solomachine.v1.DataType) |       |             |
| `data`      | [bytes](value.md#bytes)                                       |       |             |
| `timestamp` | [uint64](value.md#uint64)                                     |       |             |

### TimestampedSignatureData

TimestampedSignatureData contains the signature data and the timestamp of the signature.

| Field            | Type                           | Label | Description |
| ---------------- | ------------------------------ | ----- | ----------- |
| `signature_data` | [bytes](value.md#bytes)   |       |             |
| `timestamp`      | [uint64](value.md#uint64) |       |             |

### DataType

DataType defines the type of solo machine proof being created. This is done to preserve uniqueness of different data sign byte encodings.

| Name                                   | Number | Description                                       |
| -------------------------------------- | ------ | ------------------------------------------------- |
| DATA_TYPE_UNINITIALIZED_UNSPECIFIED | 0      | Default State                                     |
| DATA_TYPE_CLIENT_STATE              | 1      | Data type for client state verification           |
| DATA_TYPE_CONSENSUS_STATE           | 2      | Data type for consensus state verification        |
| DATA_TYPE_CONNECTION_STATE          | 3      | Data type for connection state verification       |
| DATA_TYPE_CHANNEL_STATE             | 4      | Data type for channel state verification          |
| DATA_TYPE_PACKET_COMMITMENT         | 5      | Data type for packet commitment verification      |
| DATA_TYPE_PACKET_ACKNOWLEDGEMENT    | 6      | Data type for packet acknowledgement verification |
| DATA_TYPE_PACKET_RECEIPT_ABSENCE   | 7      | Data type for packet receipt absence verification |
| DATA_TYPE_NEXT_SEQUENCE_RECV       | 8      | Data type for next sequence recv verification     |
| DATA_TYPE_HEADER                     | 9      | Data type for header verification                 |



## ibc/lightclients/tendermint/v1/tendermint.proto

### ClientState

ClientState from Tendermint tracks the current validator set, latest height, and a possible frozen height.

| Field                             | Type                                                                 | Label    | Description                                                                                                                                                                                                                                                                                                                                                                                                                         |
| --------------------------------- | -------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `chain_id`                        | [string](value.md#string)                                       |          |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `trust_level`                     | [Fraction](ibc.md#ibc.lightclients.tendermint.v1.Fraction)    |          |                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `trusting_period`                 | google.protobuf.Duration   |          | duration of the period since the LastestTimestamp during which the submitted headers are valid for upgrade                                                                                                                                                                                                                                                                                                                          |
| `unbonding_period`                | google.protobuf.Duration   |          | duration of the staking unbonding period                                                                                                                                                                                                                                                                                                                                                                                            |
| `max_clock_drift`                 | google.protobuf.Duration   |          | defines how much new (untrusted) header's Time can drift into the future.                                                                                                                                                                                                                                                                                                                                                           |
| `frozen_height`                   | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |          | Block height when the client was frozen due to a misbehaviour                                                                                                                                                                                                                                                                                                                                                                       |
| `latest_height`                   | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height) |          | Latest height the client was updated to                                                                                                                                                                                                                                                                                                                                                                                             |
| `proof_specs`                     | [ics23.ProofSpec](#ics23.ProofSpec)                     | repeated | Proof specifications used in verifying counterparty state                                                                                                                                                                                                                                                                                                                                                                           |
| `upgrade_path`                    | [string](value.md#string)                                       | repeated | Path at which next upgraded client will be committed. Each element corresponds to the key for a single CommitmentProof in the chained proof. NOTE: ClientState must stored under `{upgradePath}/{upgradeHeight}/clientState` ConsensusState must be stored under `{upgradepath}/{upgradeHeight}/consensusState` For SDK chains using the default upgrade module, upgrade_path should be []string{"upgrade", "upgradedIBCState"}` |
| `allow_update_after_expiry`       | [bool](value.md#bool)                                           |          | This flag, when set to true, will allow governance to recover a client which has expired                                                                                                                                                                                                                                                                                                                                            |
| `allow_update_after_misbehaviour` | [bool](value.md#bool)                                           |          | This flag, when set to true, will allow governance to unfreeze a client whose chain has experienced a misbehaviour event                                                                                                                                                                                                                                                                                                            |

### ConsensusState

ConsensusState defines the consensus state from Tendermint.

| Field                  | Type                                                                                 | Label | Description                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------ | ----- | -------------------------------------------------------------------------------------- |
| `timestamp`            | [google.protobuf.Timestamp](#google.protobuf.Timestamp)                 |       | timestamp that corresponds to the block height in which the ConsensusState was stored. |
| `root`                 | [ibc.core.commitment.v1.MerkleRoot](ibc.md#ibc.core.commitment.v1.MerkleRoot) |       | commitment root (i.e app hash)                                                         |
| `next_validators_hash` | [bytes](value.md#bytes)                                                         |       |                                                                                        |

### Fraction

Fraction defines the protobuf message type for tmmath.Fraction that only supports positive values.

| Field         | Type                           | Label | Description |
| ------------- | ------------------------------ | ----- | ----------- |
| `numerator`   | [uint64](value.md#uint64) |       |             |
| `denominator` | [uint64](value.md#uint64) |       |             |

### Header

Header defines the Tendermint client consensus Header. It encapsulates all the information necessary to update from a trusted Tendermint ConsensusState. The inclusion of TrustedHeight and TrustedValidators allows this update to process correctly, so long as the ConsensusState for the TrustedHeight exists, this removes race conditions among relayers The SignedHeader and ValidatorSet are the new untrusted update fields for the client. The TrustedHeight is the height of a stored ConsensusState on the client that will be used to verify the new untrusted header. The Trusted ConsensusState must be within the unbonding period of current time in order to correctly verify, and the TrustedValidators must hash to TrustedConsensusState.NextValidatorsHash since that is the last trusted validator set at the TrustedHeight.

| Field                | Type                                                                         | Label | Description |
| -------------------- | ---------------------------------------------------------------------------- | ----- | ----------- |
| `signed_header`      | [tendermint.types.SignedHeader](tendermint.types.SignedHeader) |       |             |
| `validator_set`      | [tendermint.types.ValidatorSet](tendermint.types.ValidatorSet) |       |             |
| `trusted_height`     | [ibc.core.client.v1.Height](ibc.md#ibc.core.client.v1.Height)         |       |             |
| `trusted_validators` | [tendermint.types.ValidatorSet](tendermint.types.ValidatorSet) |       |             |

### Misbehaviour

Misbehaviour is a wrapper over two conflicting Headers that implements Misbehaviour interface expected by ICS-02

| Field       | Type                                                          | Label | Description |
| ----------- | ------------------------------------------------------------- | ----- | ----------- |
| `client_id` | [string](value.md#string)                                |       |             |
| `header_1`  | [Header](ibc.md#ibc.lightclients.tendermint.v1.Header) |       |             |
| `header_2`  | [Header](ibc.md#ibc.lightclients.tendermint.v1.Header) |       |             |

