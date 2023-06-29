
## cosmos/genutil/v1beta1/genesis.proto

### GenesisState

GenesisState defines the raw genesis transaction in JSON.

| Field     | Type                         | Label    | Description                                |
| --------- | ---------------------------- | -------- | ------------------------------------------ |
| `gen_txs` | [bytes](value.md#bytes) | repeated | gen_txs defines the genesis transactions. |



## cosmos/gov/v1beta1/gov.proto

### Deposit

Deposit defines an amount deposited by an account address to an active proposal.

| Field         | Type                                                               | Label    | Description |
| ------------- | ------------------------------------------------------------------ | -------- | ----------- |
| `proposal_id` | [uint64](value.md#uint64)                                     |          |             |
| `depositor`   | [string](value.md#string)                                     |          |             |
| `amount`      | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |

### DepositParams

DepositParams defines the params for deposits on governance proposals.

| Field                | Type                                                               | Label    | Description                                                                        |
| -------------------- | ------------------------------------------------------------------ | -------- | ---------------------------------------------------------------------------------- |
| `min_deposit`        | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated | Minimum deposit for a proposal to enter voting period.                             |
| `max_deposit_period` | google.protobuf.Duration |          | Maximum period for Atom holders to deposit on a proposal. Initial value: 2 months. |

### Proposal

Proposal defines the core field members of a governance proposal.

| Field                | Type                                                                 | Label    | Description |
| -------------------- | -------------------------------------------------------------------- | -------- | ----------- |
| `proposal_id`        | [uint64](value.md#uint64)                                       |          |             |
| `content`            | google.protobuf.Any             |          |             |
| `status`             | [ProposalStatus](gov.md#cosmos.gov.v1beta1.ProposalStatus)    |          |             |
| `final_tally_result` | [TallyResult](gov.md#cosmos.gov.v1beta1.TallyResult)          |          |             |
| `submit_time`        | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |          |             |
| `deposit_end_time`   | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |          |             |
| `total_deposit`      | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin)   | repeated |             |
| `voting_start_time`  | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |          |             |
| `voting_end_time`    | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |          |             |

### TallyParams

TallyParams defines the params for tallying votes on governance proposals.

| Field            | Type                         | Label | Description                                                                                     |
| ---------------- | ---------------------------- | ----- | ----------------------------------------------------------------------------------------------- |
| `quorum`         | [bytes](value.md#bytes) |       | Minimum percentage of total stake needed to vote for a result to be considered valid.           |
| `threshold`      | [bytes](value.md#bytes) |       | Minimum proportion of Yes votes for proposal to pass. Default value: 0.5.                       |
| `veto_threshold` | [bytes](value.md#bytes) |       | Minimum value of Veto votes to Total votes ratio for proposal to be vetoed. Default value: 1/3. |

### TallyResult

TallyResult defines a standard tally for a governance proposal.

| Field          | Type                           | Label | Description |
| -------------- | ------------------------------ | ----- | ----------- |
| `yes`          | [string](value.md#string) |       |             |
| `abstain`      | [string](value.md#string) |       |             |
| `no`           | [string](value.md#string) |       |             |
| `no_with_veto` | [string](value.md#string) |       |             |

### TextProposal

TextProposal defines a standard text proposal whose changes need to be manually updated in case of approval.

| Field         | Type                           | Label | Description |
| ------------- | ------------------------------ | ----- | ----------- |
| `title`       | [string](value.md#string) |       |             |
| `description` | [string](value.md#string) |       |             |

### Vote

Vote defines a vote on a governance proposal. A Vote consists of a proposal ID, the voter, and the vote option.

| Field         | Type                                                      | Label | Description |
| ------------- | --------------------------------------------------------- | ----- | ----------- |
| `proposal_id` | [uint64](value.md#uint64)                            |       |             |
| `voter`       | [string](value.md#string)                            |       |             |
| `option`      | [VoteOption](gov.md#cosmos.gov.v1beta1.VoteOption) |       |             |

### VotingParams

VotingParams defines the params for voting on governance proposals.

| Field           | Type                                                               | Label | Description                  |
| --------------- | ------------------------------------------------------------------ | ----- | ---------------------------- |
| `voting_period` | google.protobuf.Duration |       | Length of the voting period. |

### ProposalStatus

ProposalStatus enumerates the valid statuses of a proposal.

| Name                              | Number | Description                                                                                |
| --------------------------------- | ------ | ------------------------------------------------------------------------------------------ |
| PROPOSAL_STATUS_UNSPECIFIED     | 0      | PROPOSAL_STATUS_UNSPECIFIED defines the default propopsal status.                        |
| PROPOSAL_STATUS_DEPOSIT_PERIOD | 1      | PROPOSAL_STATUS_DEPOSIT_PERIOD defines a proposal status during the deposit period.     |
| PROPOSAL_STATUS_VOTING_PERIOD  | 2      | PROPOSAL_STATUS_VOTING_PERIOD defines a proposal status during the voting period.       |
| PROPOSAL_STATUS_PASSED          | 3      | PROPOSAL_STATUS_PASSED defines a proposal status of a proposal that has passed.          |
| PROPOSAL_STATUS_REJECTED        | 4      | PROPOSAL_STATUS_REJECTED defines a proposal status of a proposal that has been rejected. |
| PROPOSAL_STATUS_FAILED          | 5      | PROPOSAL_STATUS_FAILED defines a proposal status of a proposal that has failed.          |

### VoteOption

VoteOption enumerates the valid vote options for a given governance proposal.

| Name                         | Number | Description                                                      |
| ---------------------------- | ------ | ---------------------------------------------------------------- |
| VOTE_OPTION_UNSPECIFIED    | 0      | VOTE_OPTION_UNSPECIFIED defines a no-op vote option.           |
| VOTE_OPTION_YES            | 1      | VOTE_OPTION_YES defines a yes vote option.                     |
| VOTE_OPTION_ABSTAIN        | 2      | VOTE_OPTION_ABSTAIN defines an abstain vote option.            |
| VOTE_OPTION_NO             | 3      | VOTE_OPTION_NO defines a no vote option.                       |
| VOTE_OPTION_NO_WITH_VETO | 4      | VOTE_OPTION_NO_WITH_VETO defines a no with veto vote option. |



## cosmos/gov/v1beta1/genesis.proto

### GenesisState

GenesisState defines the gov module's genesis state.

| Field                  | Type                                                            | Label    | Description                                                |
| ---------------------- | --------------------------------------------------------------- | -------- | ---------------------------------------------------------- |
| `starting_proposal_id` | [uint64](value.md#uint64)                                  |          | starting_proposal_id is the ID of the starting proposal. |
| `deposits`             | [Deposit](gov.md#cosmos.gov.v1beta1.Deposit)             | repeated | deposits defines all the deposits present at genesis.      |
| `votes`                | [Vote](gov.md#cosmos.gov.v1beta1.Vote)                   | repeated | votes defines all the votes present at genesis.            |
| `proposals`            | [Proposal](gov.md#cosmos.gov.v1beta1.Proposal)           | repeated | proposals defines all the proposals present at genesis.    |
| `deposit_params`       | [DepositParams](gov.md#cosmos.gov.v1beta1.DepositParams) |          | params defines all the paramaters of related to deposit.   |
| `voting_params`        | [VotingParams](gov.md#cosmos.gov.v1beta1.VotingParams)   |          | params defines all the paramaters of related to voting.    |
| `tally_params`         | [TallyParams](gov.md#cosmos.gov.v1beta1.TallyParams)     |          | params defines all the paramaters of related to tally.     |



## cosmos/gov/v1beta1/query.proto

### QueryDepositRequest

QueryDepositRequest is the request type for the Query/Deposit RPC method.

| Field         | Type                           | Label | Description                                                 |
| ------------- | ------------------------------ | ----- | ----------------------------------------------------------- |
| `proposal_id` | [uint64](value.md#uint64) |       | proposal_id defines the unique id of the proposal.         |
| `depositor`   | [string](value.md#string) |       | depositor defines the deposit addresses from the proposals. |

### QueryDepositResponse

QueryDepositResponse is the response type for the Query/Deposit RPC method.

| Field     | Type                                                | Label | Description                            |
| --------- | --------------------------------------------------- | ----- | -------------------------------------- |
| `deposit` | [Deposit](gov.md#cosmos.gov.v1beta1.Deposit) |       | deposit defines the requested deposit. |

### QueryDepositsRequest

QueryDepositsRequest is the request type for the Query/Deposits RPC method.

| Field         | Type                                                                                         | Label | Description                                                |
| ------------- | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `proposal_id` | [uint64](value.md#uint64)                                                               |       | proposal_id defines the unique id of the proposal.        |
| `pagination`  | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryDepositsResponse

QueryDepositsResponse is the response type for the Query/Deposits RPC method.

| Field        | Type                                                                                           | Label    | Description                                        |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `deposits`   | [Deposit](gov.md#cosmos.gov.v1beta1.Deposit)                                            | repeated |                                                    |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryParamsRequest

QueryParamsRequest is the request type for the Query/Params RPC method.

| Field         | Type                           | Label | Description                                                                                          |
| ------------- | ------------------------------ | ----- | ---------------------------------------------------------------------------------------------------- |
| `params_type` | [string](value.md#string) |       | params_type defines which parameters to query for, can be one of "voting", "tallying" or "deposit". |

### QueryParamsResponse

QueryParamsResponse is the response type for the Query/Params RPC method.

| Field            | Type                                                            | Label | Description                                                |
| ---------------- | --------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `voting_params`  | [VotingParams](gov.md#cosmos.gov.v1beta1.VotingParams)   |       | voting_params defines the parameters related to voting.   |
| `deposit_params` | [DepositParams](gov.md#cosmos.gov.v1beta1.DepositParams) |       | deposit_params defines the parameters related to deposit. |
| `tally_params`   | [TallyParams](gov.md#cosmos.gov.v1beta1.TallyParams)     |       | tally_params defines the parameters related to tally.     |

### QueryProposalRequest

QueryProposalRequest is the request type for the Query/Proposal RPC method.

| Field         | Type                           | Label | Description                                         |
| ------------- | ------------------------------ | ----- | --------------------------------------------------- |
| `proposal_id` | [uint64](value.md#uint64) |       | proposal_id defines the unique id of the proposal. |

### QueryProposalResponse

QueryProposalResponse is the response type for the Query/Proposal RPC method.

| Field      | Type                                                  | Label | Description |
| ---------- | ----------------------------------------------------- | ----- | ----------- |
| `proposal` | [Proposal](gov.md#cosmos.gov.v1beta1.Proposal) |       |             |

### QueryProposalsRequest

QueryProposalsRequest is the request type for the Query/Proposals RPC method.

| Field             | Type                                                                                         | Label | Description                                                 |
| ----------------- | -------------------------------------------------------------------------------------------- | ----- | ----------------------------------------------------------- |
| `proposal_status` | [ProposalStatus](gov.md#cosmos.gov.v1beta1.ProposalStatus)                            |       | proposal_status defines the status of the proposals.       |
| `voter`           | [string](value.md#string)                                                               |       | voter defines the voter address for the proposals.          |
| `depositor`       | [string](value.md#string)                                                               |       | depositor defines the deposit addresses from the proposals. |
| `pagination`      | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request.  |

### QueryProposalsResponse

QueryProposalsResponse is the response type for the Query/Proposals RPC method.

| Field        | Type                                                                                           | Label    | Description                                        |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `proposals`  | [Proposal](gov.md#cosmos.gov.v1beta1.Proposal)                                          | repeated |                                                    |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### QueryTallyResultRequest

QueryTallyResultRequest is the request type for the Query/Tally RPC method.

| Field         | Type                           | Label | Description                                         |
| ------------- | ------------------------------ | ----- | --------------------------------------------------- |
| `proposal_id` | [uint64](value.md#uint64) |       | proposal_id defines the unique id of the proposal. |

### QueryTallyResultResponse

QueryTallyResultResponse is the response type for the Query/Tally RPC method.

| Field   | Type                                                        | Label | Description                        |
| ------- | ----------------------------------------------------------- | ----- | ---------------------------------- |
| `tally` | [TallyResult](gov.md#cosmos.gov.v1beta1.TallyResult) |       | tally defines the requested tally. |

### QueryVoteRequest

QueryVoteRequest is the request type for the Query/Vote RPC method.

| Field         | Type                           | Label | Description                                         |
| ------------- | ------------------------------ | ----- | --------------------------------------------------- |
| `proposal_id` | [uint64](value.md#uint64) |       | proposal_id defines the unique id of the proposal. |
| `voter`       | [string](value.md#string) |       | voter defines the oter address for the proposals.   |

### QueryVoteResponse

QueryVoteResponse is the response type for the Query/Vote RPC method.

| Field  | Type                                          | Label | Description                    |
| ------ | --------------------------------------------- | ----- | ------------------------------ |
| `vote` | [Vote](gov.md#cosmos.gov.v1beta1.Vote) |       | vote defined the queried vote. |

### QueryVotesRequest

QueryVotesRequest is the request type for the Query/Votes RPC method.

| Field         | Type                                                                                         | Label | Description                                                |
| ------------- | -------------------------------------------------------------------------------------------- | ----- | ---------------------------------------------------------- |
| `proposal_id` | [uint64](value.md#uint64)                                                               |       | proposal_id defines the unique id of the proposal.        |
| `pagination`  | [cosmos.base.query.v1beta1.PageRequest](base.md#cosmos.base.query.v1beta1.PageRequest) |       | pagination defines an optional pagination for the request. |

### QueryVotesResponse

QueryVotesResponse is the response type for the Query/Votes RPC method.

| Field        | Type                                                                                           | Label    | Description                                        |
| ------------ | ---------------------------------------------------------------------------------------------- | -------- | -------------------------------------------------- |
| `votes`      | [Vote](gov.md#cosmos.gov.v1beta1.Vote)                                                  | repeated | votes defined the queried votes.                   |
| `pagination` | [cosmos.base.query.v1beta1.PageResponse](base.md#cosmos.base.query.v1beta1.PageResponse) |          | pagination defines the pagination in the response. |

### Query

Query defines the gRPC querier service for gov module

| Method Name   | Request Type                                                                        | Response Type                                                                         | Description                                                               | HTTP Verb | Endpoint                                                          |
| ------------- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | --------- | ----------------------------------------------------------------- |
| `Proposal`    | [QueryProposalRequest](gov.md#cosmos.gov.v1beta1.QueryProposalRequest)       | [QueryProposalResponse](gov.md#cosmos.gov.v1beta1.QueryProposalResponse)       | Proposal queries proposal details based on ProposalID.                    | GET       | /cosmos/gov/v1beta1/proposals/{proposal_id}                      |
| `Proposals`   | [QueryProposalsRequest](gov.md#cosmos.gov.v1beta1.QueryProposalsRequest)     | [QueryProposalsResponse](gov.md#cosmos.gov.v1beta1.QueryProposalsResponse)     | Proposals queries all proposals based on given status.                    | GET       | /cosmos/gov/v1beta1/proposals                                     |
| `Vote`        | [QueryVoteRequest](gov.md#cosmos.gov.v1beta1.QueryVoteRequest)               | [QueryVoteResponse](gov.md#cosmos.gov.v1beta1.QueryVoteResponse)               | Vote queries voted information based on proposalID, voterAddr.            | GET       | /cosmos/gov/v1beta1/proposals/{proposal_id}/votes/{voter}        |
| `Votes`       | [QueryVotesRequest](gov.md#cosmos.gov.v1beta1.QueryVotesRequest)             | [QueryVotesResponse](gov.md#cosmos.gov.v1beta1.QueryVotesResponse)             | Votes queries votes of a given proposal.                                  | GET       | /cosmos/gov/v1beta1/proposals/{proposal_id}/votes                |
| `Params`      | [QueryParamsRequest](gov.md#cosmos.gov.v1beta1.QueryParamsRequest)           | [QueryParamsResponse](gov.md#cosmos.gov.v1beta1.QueryParamsResponse)           | Params queries all parameters of the gov module.                          | GET       | /cosmos/gov/v1beta1/params/{params_type}                         |
| `Deposit`     | [QueryDepositRequest](gov.md#cosmos.gov.v1beta1.QueryDepositRequest)         | [QueryDepositResponse](gov.md#cosmos.gov.v1beta1.QueryDepositResponse)         | Deposit queries single deposit information based proposalID, depositAddr. | GET       | /cosmos/gov/v1beta1/proposals/{proposal_id}/deposits/{depositor} |
| `Deposits`    | [QueryDepositsRequest](gov.md#cosmos.gov.v1beta1.QueryDepositsRequest)       | [QueryDepositsResponse](gov.md#cosmos.gov.v1beta1.QueryDepositsResponse)       | Deposits queries all deposits of a single proposal.                       | GET       | /cosmos/gov/v1beta1/proposals/{proposal_id}/deposits             |
| `TallyResult` | [QueryTallyResultRequest](gov.md#cosmos.gov.v1beta1.QueryTallyResultRequest) | [QueryTallyResultResponse](gov.md#cosmos.gov.v1beta1.QueryTallyResultResponse) | TallyResult queries the tally of a proposal vote.                         | GET       | /cosmos/gov/v1beta1/proposals/{proposal_id}/tally                |



## cosmos/gov/v1beta1/tx.proto

### MsgDeposit

MsgDeposit defines a message to submit a deposit to an existing proposal.

| Field         | Type                                                               | Label    | Description |
| ------------- | ------------------------------------------------------------------ | -------- | ----------- |
| `proposal_id` | [uint64](value.md#uint64)                                     |          |             |
| `depositor`   | [string](value.md#string)                                     |          |             |
| `amount`      | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |

### MsgDepositResponse

MsgDepositResponse defines the Msg/Deposit response type.

### MsgSubmitProposal

MsgSubmitProposal defines an sdk.Msg type that supports submitting arbitrary proposal Content.

| Field             | Type                                                               | Label    | Description |
| ----------------- | ------------------------------------------------------------------ | -------- | ----------- |
| `content`         | google.protobuf.Any           |          |             |
| `initial_deposit` | [cosmos.base.v1beta1.Coin](base.md#cosmos.base.v1beta1.Coin) | repeated |             |
| `proposer`        | [string](value.md#string)                                     |          |             |

### MsgSubmitProposalResponse

MsgSubmitProposalResponse defines the Msg/SubmitProposal response type.

| Field         | Type                           | Label | Description |
| ------------- | ------------------------------ | ----- | ----------- |
| `proposal_id` | [uint64](value.md#uint64) |       |             |

### MsgVote

MsgVote defines a message to cast a vote.

| Field         | Type                                                      | Label | Description |
| ------------- | --------------------------------------------------------- | ----- | ----------- |
| `proposal_id` | [uint64](value.md#uint64)                            |       |             |
| `voter`       | [string](value.md#string)                            |       |             |
| `option`      | [VoteOption](gov.md#cosmos.gov.v1beta1.VoteOption) |       |             |

### MsgVoteResponse

MsgVoteResponse defines the Msg/Vote response type.

### Msg

Msg defines the bank Msg service.

| Method Name      | Request Type                                                            | Response Type                                                                           | Description                                                             | HTTP Verb | Endpoint |
| ---------------- | ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | --------- | -------- |
| `SubmitProposal` | [MsgSubmitProposal](gov.md#cosmos.gov.v1beta1.MsgSubmitProposal) | [MsgSubmitProposalResponse](gov.md#cosmos.gov.v1beta1.MsgSubmitProposalResponse) | SubmitProposal defines a method to create new proposal given a content. |           |          |
| `Vote`           | [MsgVote](gov.md#cosmos.gov.v1beta1.MsgVote)                     | [MsgVoteResponse](gov.md#cosmos.gov.v1beta1.MsgVoteResponse)                     | Vote defines a method to add a vote on a specific proposal.             |           |          |
| `Deposit`        | [MsgDeposit](gov.md#cosmos.gov.v1beta1.MsgDeposit)               | [MsgDepositResponse](gov.md#cosmos.gov.v1beta1.MsgDepositResponse)               | Deposit defines a method to add deposit on a specific proposal.         |           |          |

