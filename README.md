# ERC20 in Assembly

### This is an explanation of the modified version of the ERC20 token implementation


const create2 = await steps.create2({ session, execute: true }) // deploy create2
const resolver = await steps.resolver({ session, create2, salt: 0n, nonce: 1n, execute: true }) // deploy resolver
const erc20 = await steps.erc20({ session, create2, salt: 1n, nonce: 2n, execute: true }) // deploy erc20
await steps.erc20_link({ session, resolver, erc20, nonce: 0n, execute: true }) // link erc20
const dzhv = await steps.dzhv({ session, create2, salt: 2n, resolver, nonce: 3n, execute: true }) // deploy dzhv
await steps.mint({ session, dzhv, dies, nonce: 2n, execute: true }) // initial mint
