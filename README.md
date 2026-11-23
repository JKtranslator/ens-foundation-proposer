# KPK proposer for the ENS Foundation Safe

A single page that lets an owner of the ENS Foundation Safe register KPK's proposer Safe as a
proposer, by signing one message in a browser wallet.

**Live page:** https://jktranslator.github.io/ens-foundation-proposer/

| | |
|---|---|
| ENS Foundation Safe | `0x9C7dB6B1085ec4D07f75c0BD91AD3FcD368fA19E` (3 of 5) |
| Proposer being added | `0xB1C6402137A3531c9E2d63985E0B76968C8243E8`, "ENS Proposer - KPK managed" (2 of 6) |

A proposer can place transactions in the Safe's queue for its signers to review. It cannot sign,
approve or execute them. Nothing is sent on-chain and there is no gas fee.

Safe{Wallet} does not accept a smart contract account as a proposer. Safe's Queue Service, which
took proposers over from the Transaction Service in November 2026, does when a current owner of the
Safe signs for it; the page sends that signature to it directly (`POST
https://api.safe.global/queue/api/v1/delegates`, typed data domain `{name: "Safe Queue Service",
version: "1.0", chainId: 1, safe: <Foundation Safe>}`, message `{delegateAddress, totp, action: "add"}`;
a 409 means the proposer is already registered by that owner).

The page is one self-contained HTML file. It holds no keys, stores nothing, and talks only to
`api.safe.global` and a public Ethereum node. The two addresses are fixed in the file, so a link
cannot be altered to register a different proposer.

Prepared by KPK.
