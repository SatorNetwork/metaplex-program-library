# Overview

This document describes how to make custom isolated Metaplex Storefront program.


## Replace program id

Find `p1exdMJcjVao65QdewkaZRUnU6VPSXhus9n2GzWfh98` and replace with custom `SatorUC6nwv6NtcxAMKaybPP1jCgvGHVtLEV4MZsRE5`

Run airdrop for keypair of program:
```s 
solana airdrop 2 --keypair ../../.solana/sator/satoRPiZcEeYUkGLfR6rURgFswucXZLkU4iqrbkd55H.json --url devnet
```

Deploy to devnet:
```shell
solana program deploy --keypair ../../.solana/sator/satoRPiZcEeYUkGLfR6rURgFswucXZLkU4iqrbkd55H.json --url devnet ../../target/deploy/mpl_metaplex.so --program-id ../../.solana/sator/SatorUC6nwv6NtcxAMKaybPP1jCgvGHVtLEV4MZsRE5.json
```

As you replaced `config.programs.metaplex` value, see it is used in as `MetaplexProgram.PUBKEY` in js of metaplex store sdk. So you have either publish or `yalc` for storeront.

Metaplex is root program, nobody calls it. 

in `metaplex-foundation/metaplex` replace `METAPLEX_ID` with id too.

In `metaplex-foundation/js` replace `MetaplexProgram.PUBKEY`. 

If JS seems has nested hierarchy need to replace to get proper ID.

After that follow steps here and get fully working isolated market places

https://docs.metaplex.com/storefront/installation

`nft-packs` program (mystery box drops) depends on metaplex, but that can be built later as feature will be required.

## Good

- Get best of ecosystem with updates (ui, fixes, tools, etc.)
- Fast load time of web site
- Eventually can send path to `metaplex-foundation` to allow override that id across all packages
- Metaplex Store front has adaptive design(works well on mobile).
- Reskining is existing practice here
- Auctions, mint tools and other things are ready made.
- Branded keys with `Sator` prefix:)

## Bad 

- Need to maintain forks of all and deploys and CI
- But you already forked JS anyway as part of Metaplex Storefront


## Security

For deployment of program better setup verified mutlisingatures deploys.
