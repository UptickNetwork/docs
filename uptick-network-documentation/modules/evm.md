# EVM

#### Available Commands

| Name    | Description                                              |
| ------- | -------------------------------------------------------- |
| raw     | Build cosmos transaction from raw ethereum transaction.  |
| code    | Gets code from an account.                               |
| params  | Get the evm params.                                      |
| storage | Gets storage for an account with a given key and height. |

#### uptickd tx evm raw

Build cosmos transaction from raw ethereum transaction.

```Bash
uptickd tx evm raw TX_HEX [flags]
```

#### uptickd q evm code

Gets code from an account.

```Bash
uptickd query evm code ADDRESS [flags]
```

#### uptickd q evm params

Get the evm params.

```Bash
uptickd q evm params
```

#### uptickd q evm storage

Gets storage for an account with a given key and height.

```Bash
uptickd query evm storage ADDRESS KEY [flags]
```
