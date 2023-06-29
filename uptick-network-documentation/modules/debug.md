---
description: A tool for simple debugging.
---

# Debug

#### Available Commands

| Name      | Description                                           |
| --------- | ----------------------------------------------------- |
| addr      | Convert an address between hex and bech32             |
| ibc-denom | Generate ibc denom name                               |
| pubkey    | Decode a pubkey from proto JSON                       |
| raw-bytes | Convert raw bytes output (eg. \[10 21 13 255]) to hex |

#### uptickd debug addr

```Bash
uptickd debug addr uptick1sual70ma3pltk7zjdf6x4e7m6g3hpg6grm33fa
```

returns

```Python
Address bytes: [135 59 255 63 125 136 126 187 120 82 106 116 106 231 219 210 35 112 163 72]
Address (hex): 873BFF3F7D887EBB78526A746AE7DBD22370A348
Address (EIP-55): 0x873bff3f7d887ebB78526a746AE7dBd22370a348
Bech32 Acc: uptick1sual70ma3pltk7zjdf6x4e7m6g3hpg6grm33fa
Bech32 Val: uptickvaloper1sual70ma3pltk7zjdf6x4e7m6g3hpg6gsry993
```

#### uptickd debug pubkeyThe following give the same result:

```Bash
uptickd debug pubkey '{"@type":"/ethermint.crypto.v1.ethsecp256k1.PubKey","key":"Ap7nv/2XZ0aok7Kd8HfW/4XxtsECCl0RqITh7t7j7f2S"}'
```

returns

```
Address (EIP-55): 0x873bff3f7d887ebB78526a746AE7dBd22370a348
Bech32 Acc: uptick1sual70ma3pltk7zjdf6x4e7m6g3hpg6grm33fa
PubKey Hex: 029ee7bffd976746a893b29df077d6ff85f1b6c1020a5d11a884e1eedee3edfd92
```

#### uptickd debug raw-bytes

Convert raw bytes output (eg.\[72 101 108 108 111 44 32 112 108 97 121 103 114 111 117 110 100])

```Bash
uptickd debug raw-bytes <raw-bytes>
uptickd debug raw-bytes '[72 101 108 108 111 44 32 112 108 97 121 103 114 111 117 110 100]'
```

returns

```Python
48656C6C6F2C20706C617967726F756E64
```
