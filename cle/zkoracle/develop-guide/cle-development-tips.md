# CLE Development Tips

### Development

* When developing with storage as data source, you can use the following tools for visualization of storage slot layout:
  * [evm.storage](https://evm.storage/) for mainnet
  * [storagoor](https://storagoor.vercel.app/) for sepolia
  * [smart contract storage viewer](https://tintinweb.github.io/smart-contract-storage-viewer/)
  * [storage layout option of Solidity compiler](https://arc.net/l/quote/phcauzke)
* When developing with a deployed smart contract, you can use the following tools for examining its source code onchain and its current data:
  * [ContractReader](https://www.contractreader.io/) for reading contract's current data
  * [codeslaw](https://www.codeslaw.app/) for reading contract's source code
  * [Parsec](https://parsec.fi/) and [Arkham](https://www.arkhamintelligence.com/) as better alternatives to Etherscan
* Provable program needs to be compilable and runnable in normal execution runtime first.

```typescript
// Code not compilable (due to reassign `state` which is constant)
export function handleBlocks(blocks: Block[]): Bytes {
  const state = new Bytes(0);
  state = new Bytes(0);
  return state;
}

// Code not executable or runnable (due to divide number by zero)
export function handleBlocks(blocks: Block[]): Bytes {
  const state = new Bytes(0);
  const NAN = BigInt.fromI32(0).div(0);
  return state;
}
```

* For generating proof on zkVM, do not use io syscalls like `console` etc. `console.log(string)` (note that only `string` type is supported in AssemblyScript) should only be used in debug stage.

```typescript
export function handleBlocks(blocks: Block[]): Bytes {
  let state = new Bytes(0);
  // Won't be compiled, because type not supported in AssemblyScript
  console.log(state);
  // Will be executed, but won't be proved successfully.
  console.log(state.toString());
  return state;
}
```

* The best practice when finishing up a CLE is documenting everything (block number used for testing execution and proof generation, example output, zkVM image url...), so that others can replicate the whole flow.

### Optimization

* Look at (approximate) WASM cost for each operation! More complex logic (eg. anything with lots of `if` statements or `string`) usally means more instructions, which means longer proof generation time.

```typescript
// WASM cost: 65 line of wat.
Bytes.padStart(targetLength: i32, padDigit: u8 = 0): Bytes

// WASM cost: 1177 lines of wat.
BigInt.toString(radix: i32 = 10): string
```

* Don't use template literals (`${}`), for example when throwing errors, because it will be compiled to too many WASM instructions (\~1000 diff).

```typescript
// 2547 lines in generated .wat file with template literal
export function handleBlocks(blocks: Block[]): Bytes {
  let state = new Bytes(0);
  if (state.length != 0) {
    throw new Error(`Invalid state length: ${state.length}, expected 0 bytes.`);
  }
  return state;
}

// 2179 lines in generated .wat file without template literal
export function handleBlocks(blocks: Block[]): Bytes {
  let state = new Bytes(0);
  if (state.length != 0) {
    throw new Error(`Invalid state length, expected 0 bytes.`);
  }
  return state;
}
```

* Try not to use keywords that may introduce extra global init code e.g. `new`, `static` etc. `changetype` is fine, [because](https://github.com/AssemblyScript/assemblyscript/issues/549#issuecomment-474005579) it just changes the type statically and does not result in any actual instructions.
* You can use third-party optimization tools (such as [wasm-opt](https://www.npmjs.com/package/wasm-opt), [wasm-size-inspector](https://wasm-size-inspector.vercel.app/)) to reduce WASM binary size and optimize.
