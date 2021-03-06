---
title: TokenType1
icon: circle
ordinal: 5
---

### `create`

Create a new SLP Token of Type 1

#### Arguments

1.  createConfig `Object` required

##### Valid config properties

- `fundingAddress`: `String`. legacy, cash or slp address format
- `fundingWif`: `String`. : compressed WIF format. Available via `SLP.HDNode.toWIF`
- `tokenReceiverAddress` : `String`. legacy, cash or slp address format
- `batonReceiverAddress`: `String`. legacy, cash or slp address format. The address which has the baton has the ability to mint more tokens.
- `bchChangeReceiverAddress` : `String.` legacy, cash or slp address format
- `decimals`: `Number`. Number of decimal points for your token
- `name` : `String`. Name of token
- `symbol` : `String`. Token symbol
- `documentUri` : `String`. URI of token document
- `documentHash` : `String`. Hash of token document
- `initialTokenQty` : `Number`. Initial token quantity

#### Result

tokenId `String`. The tokenId of your newly created token. This tokenId is the txid of the genesis tx. You will use this tokenId as your token's unique identifier and to mint future tokens

#### Examples

    (async function() {
      let token = await SLP.TokenType1.create({
        fundingAddress: 'bitcoincash:qpdg4wtc96zucm6qzvnwwskfu7h4l9wapgmz3jwdm7',
        fundingWif: 'KxW2CYJ78Tf1fJNYZcoKhGuKD4Gf5qsBEFgLpVFMtZJLSDCRkpXD',
        tokenReceiverAddress: '19Fk11eyDcou66eTQ1ovTXJj7BsJTgsfo1',
        batonReceiverAddress:
          'simpleledger:qpdg4wtc96zucm6qzvnwwskfu7h4l9wapghe6fmd9q',
        bchChangeReceiverAddress:
          '19Fk11eyDcou66eTQ1ovTXJj7BsJTgsfo1',
        decimals: 2,
        name: 'Test SLP SDK Token 3',
        symbol: 'TEST3',
        documentUri: 'badger@bitcoin.com',
        documentHash: null,
        initialTokenQty: 1234,
      })
      console.log(token)
    })()

    // returns
    703920f578d36d975ffdee428df822557c6e9313ceda0d28ad837ebbf2007327

### `mint`

Mint additional tokens of Type 1

#### Arguments

1.  mintConfig `Object` required

##### Valid config properties

- `fundingAddress`: `String`. legacy, cash or slp address format
- `fundingWif`: `String`. : compressed WIF format. Available via `SLP.HDNode.toWIF`
- `tokenReceiverAddress` : `String`. legacy, cash or slp address format
- `batonReceiverAddress`: `String`. legacy, cash or slp address format
- `bchChangeReceiverAddress` : `String.` legacy, cash or slp address format
- `tokenId`: `String`. tokenId of token to mint more of
- `additionalTokenQty`: `Number`. Number of additional tokens to mint

#### Result

mintId `String`. The txid of the newly minted tokens

#### Examples

    (async function() {
      let mint = await SLP.TokenType1.mint({
        fundingAddress: '19Fk11eyDcou66eTQ1ovTXJj7BsJTgsfo1',
        fundingWif: 'KxW2CYJ78Tf1fJNYZcoKhGuKD4Gf5qsBEFgLpVFMtZJLSDCRkpXD',
        tokenReceiverAddress: '1G84HH1zJLQq6akzzHYJVnTEYhiqkHpNtZ',
        batonReceiverAddress:
          'bitcoincash:qzjalztem05hahspdkrqr529me4f7h27zyqu20smfq',
        bchChangeReceiverAddress:
          'simpleledger:qzjalztem05hahspdkrqr529me4f7h27zyv8p59mh7',
        tokenId: '703920f578d36d975ffdee428df822557c6e9313ceda0d28ad837ebbf2007327',
        additionalTokenQty: 100,
      })
      console.log(mint)
    })()

    // returns
    26a3eb17e11a732bbfd2fdf45bd1f21e9ffebe79b2fe6d2ad229481be38f1f85

### `send`

Send tokens of Type 1

#### Arguments

1.  sendConfig `Object` required

##### Valid config properties

- `fundingAddress`: `String`. legacy, cash or slp address format
- `fundingWif`: `String`. : compressed WIF format. Available via `SLP.HDNode.toWIF`
- `tokenReceiverAddress` : `String`. legacy, cash or slp address format
- `bchChangeReceiverAddress` : `String.` legacy, cash or slp address format
- `tokenId`: `String`. tokenId of token to send
- `amount`: `Number`. Number of tokens to send

#### Result

sendId `String`. The txid of your sent tokens

#### Examples

    (async function() {
      let send = await SLP.TokenType1.send({
        fundingAddress: '1G84HH1zJLQq6akzzHYJVnTEYhiqkHpNtZ',
        fundingWif: 'KyuyWyx7gJC6SMsRTkMgJcRCXhoQ7gqxJdGUEybWx7Uu8197ToqE',
        tokenReceiverAddress: 'simpleledger:qzczwp9wnej8mhel4me5v2rv20x95d6yyglncxdgtr',
        bchChangeReceiverAddress:
          'simpleledger:qzczwp9wnej8mhel4me5v2rv20x95d6yyglncxdgtr',
        tokenId: '703920f578d36d975ffdee428df822557c6e9313ceda0d28ad837ebbf2007327',
        amount: 10,
      })
      console.log(send)
    })()

    // returns
    76fb0f1d3d8a010720f8f24c19476e16fa96735e5c215b12773a65608017bd25

### `burn`

Burn an amount of tokens for an address by tokenId

**CAUTION: THIS WILL BURN AN AMOUNT OF YOUR TOKENS FOR A TOKENID. PLEASE USE WITH CARE**

#### Arguments

1.  burnConfig `Object` required

##### Valid config properties

- `fundingAddress`: `String`. legacy, cash or slp address format
- `fundingWif`: `String`. : compressed WIF format. Available via `SLP.HDNode.toWIF`
- `tokenId`: `String`. tokenId of token to burn all of
- `bchChangeReceiverAddress` : `String`. legacy, cash or slp address format
- `amount`: `Number`. Amount of tokens to burn

#### Result

txid `String`. The txid of your burned tokens

#### Examples

    (async () => {
      try {
        let iBurnConfig = {
          fundingAddress: "bchtest:qp5e2laasex4m2qkrtel3skamsftvu0gaswsmdxcd2",
          fundingWif: "cQS4N8Jbw9bmoWiVmprVEs5dEeJ6oUE2FxUo5VSvsDQSBfXakrVc",
          tokenId:
            "4c7d9c4f50f99ec0d21213d51b09e2c5199e18d88bf2f4a809f164601eda0e1b",
          amount: 500,
          bchChangeReceiverAddress:
            "bchtest:qp5e2laasex4m2qkrtel3skamsftvu0gaswsmdxcd2"
        };
        let burn = await SLP.TokenType1.burn(iBurnConfig);
        console.log(burn);
      } catch (error) {
        console.error(error);
      }
    })();

    // returns
    30785e55da16be11ce849805abb6d058cfc2f76057627a36a34d3855e678489c

### `burnAll`

Burn all tokens for an address by tokenId

**CAUTION: THIS WILL BURN ALL OF YOUR TOKENS FOR A TOKENID. PLEASE USE WITH CARE**

#### Arguments

1.  burnAllConfig `Object` required

##### Valid config properties

- `fundingAddress`: `String`. legacy, cash or slp address format
- `fundingWif`: `String`. : compressed WIF format. Available via `SLP.HDNode.toWIF`
- `tokenId`: `String`. tokenId of token to burn all of
- `bchChangeReceiverAddress` : `String.` legacy, cash or slp address format

#### Result

txid `String`. The txid of your burned tokens

#### Examples

    (async () => {
      try {
        let iBurnAllConfig = {
          fundingAddress: "bchtest:qqjfqa7qsmydeuctqvddppjnkr53vchseuv49mhsxa",
          fundingWif: "cNbbGFfSG8xvrH4HXJLcoENEmtkDAvPoC21qVhjntUc18XBzhGGe",
          tokenId:
            "3125ee6e4b051a19996a58cd876dade21a0a891d16845ada7d441573805c08db",
          bchChangeReceiverAddress: "bchtest:qp5e2laasex4m2qkrtel3skamsftvu0gaswsmdxcd2"
        };
        let burnAll = await SLP.TokenType1.burnAll(iBurnAllConfig);
        console.log(burnAll);
      } catch (error) {
        console.error(error);
      }
    })();

    // returns
    8d2a6aad3de38e79718c043c6f83a960807787efec92d6a1d9940e2ed04d2169
