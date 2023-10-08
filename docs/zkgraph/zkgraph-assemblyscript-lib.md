---
description: https://github.com/hyperoracle/zkgraph-lib
---

# zkGraph AssemblyScript Lib

{% hint style="info" %}
For Subgraph-compatibility, the design of this library follows the AssemblyScript API by The Graph.
{% endhint %}

zkGraph AssemblyScript Library provides essential data structure for development:

* `Event` of Ethereum in AssemblyScript
* `ByteArray` in AssemblyScript
* `Bytes` in AssemblyScript
* `BigInt` in AssemblyScript
* …

`zkgraph-lib` is the default option for zkGraph development with all functions tested in execution and proving environment. You can also install and use other libs such as `as-bigint`, or `as-sha256`, or simply write your own like [this](https://github.com/LiRiu/zkUsecases/blob/norman/example/opensea/mapping.ts#L3).

### Library Reference

#### **Address**

`import { Address } from from "@hyperoracle/zkgraph-lib"`

`Address` extends `Bytes` to represent Ethereum `address` values.

It adds the following method on top of the `Bytes` API:

* `Address.fromString(s: string): Address` – Creates an `Address` from a hexadecimal string.
* `Address.fromBytes(b: Bytes): Address` – Creates an `Address` from `b` which must be exactly 20 bytes long. Passing in a value with fewer or more bytes will result in an error.
* `Address.zero(): Address` - Create an `Address` with zeroes.

#### **BigInt**

`import { BigInt } from "@hyperoracle/zkgraph-lib"`

`BigInt` is used to represent big integers. This includes Ethereum values of type `uint32` to `uint256` and `int64` to `int256`. Everything below `uint32`, such as `int32`, `uint24` or `int8` is represented as `i32`.

The `BigInt` class has the following API:

_Construction_

* `BigInt.fromI32(x: i32): BigInt` – Creates a `BigInt` from an `i32`.
* `BigInt.fromU32(x: u32): BigInt` – Creates a `BigInt` from a `u32`.
* `BigInt.fromI64(x: i64): BigInt` – Creates a `BigInt` from an `i64`.
* `BigInt.fromU64(x: u64): BigInt` – Creates a `BigInt` from a `u64`.
* `BigInt.zero(x: u64): BigInt` – Creates a `BigInt` that is zero.
* `BigInt.fromString(s: string): BigInt`– Parses a `BigInt` from a string.
* `BigInt.fromBytes(x: Bytes, isNegative: boolean = false): BigInt`– Parses a `BigInt` from a `Bytes` with little-endian order.
* `BigInt.fromBytesBigEndian(x: Bytes, isNegative: boolean = false): BigInt`– Parses a `BigInt` from a `Bytes` with big-endian order.

_Type conversions_

* `x.toHex(): string` – Turns `BigInt` into a string of hexadecimal characters.
* `x.toHexString(prefix: string = ""): string` – Turns `BigInt` into a string of hexadecimal characters, with optional prefix default to empty.
* `x.toString(radix: i32 = 10): string` – Turns `BigInt` into a string based on given radix.
* `x.toI32(): i32` – Returns the `BigInt` as an `i32`; fails if the value does not fit into `i32`. It's a good idea to first check `x.isI32()`.
* `x.toU32(): u32` – Returns the `BigInt` as a `u32`.
* `x.toI64(): i64` – Returns the `BigInt` as an `i64`.
* `x.toU64(): u64` – Returns the `BigInt` as a `u64`.

_Math_

Syntax like `x.plus(b)` is recommended instead of `a + b` to avoid compiler warning.

* `x.plus(y: BigInt): BigInt` – Can be written as `x + y`, or `add`.
* `x.minus(y: BigInt): BigInt` – Can be written as `x - y`, or `sub`.
* `x.times(y: BigInt): BigInt` – Can be written as `x * y`, or `mul`.
* `x.div(y: BigInt): BigInt` – Can be written as `x / y`.
* `x.mod(y: BigInt): BigInt` – Can be written as `x % y`.
* `x.equals(y: BigInt): bool` – Can be written as `x == y`, or `eq`.
* `x.notEqual(y: BigInt): bool` – Can be written as `x != y`, or `ne`.
* `x.lt(y: BigInt): bool` – Can be written as `x < y`.
* `x.le(y: BigInt): bool` – Can be written as `x <= y`, or `lte`.
* `x.gt(y: BigInt): bool` – Can be written as `x > y`.
* `x.ge(y: BigInt): bool` – Can be written as `x >= y`, or `gte`.
* `x.neg(): BigInt` – Can be written as `-x`.
* `x.abs(): BigInt` – Absolute value.
* `x.square(): BigInt` – Square.
* `x.pow(exp: i32): BigInt` – Exponentiation.
* `x.sqrt(): BigInt` – Square root. Note that this may be computationally expensive in zkVM.

_Bitwise Operation_

* `x.bitOr(y: BigInt): BigInt` – Can be written as `x | y`, or `BigInt.bitOr(x, y)`.
* `x.bitXor(y: BigInt): BigInt` – Can be written as `x ^ y`, or `BigInt.bitXor(x, y)`.
* `x.bitAnd(y: BigInt): BigInt` – Can be written as `x & y`, or `BigInt.bitAnd(x, y)`.
* `x.bitNot(): BigInt` – Can be written as `~x`, or `BigInt.bitNot(x)`.&#x20;
* `leftShift(k: i32): BigInt` – Can be written as `x << y`.
* `rightShift(k: i32): BigInt` – Can be written as `x >> y`.

_Others_

* `x.copy(): BigInt` – Returns a copy of `x`.
* `compare(x: BigInt, y: BigInt): i32` - Returns 1 if x > y, -1 if x < y, and 0 if x == y.
* `x.isI32(): bool` – Check if the number fits in an `i32`.
* `x.isZero(): bool` – Convenience for checking if the number is zero.
* `x.isOdd(): bool` – Check if the number is odd.

#### **ByteArray**

`import { ByteArray } from "@hyperoracle/zkgraph-lib"`

`ByteArray` represents an array of `u8`.

You may need to use `BigEndian` version functions for Ethereum data structures.

_Construction_

* `ByteArray.fromI32(x: i32): ByteArray` - Decomposes `x` into bytes.
* `ByteArray.fromI32BigEndian(x: i32): ByteArray` - Decomposes `x` into bytes in BigEndian.
* `ByteArray.fromU32(x: u32): ByteArray` - Decomposes `x` into bytes.
* `ByteArray.fromU32BigEndian(x: u32): ByteArray` - Decomposes `x` into bytes in BigEndian.
* `ByteArray.fromI64(x: i64): ByteArray` - Decomposes `x` into bytes.
* `ByteArray.fromI64BigEndian(x: i64): ByteArray` - Decomposes `x` into bytes in BigEndian.
* `ByteArray.fromU64(x: u64): ByteArray` - Decomposes `x` into bytes.
* `ByteArray.fromU64BigEndian(x: u64): ByteArray` - Decomposes `x` into bytes in BigEndian.
* `ByteArray.fromHexString(hex: string): ByteArray` - Input length must be even. Prefixing with `0x` is optional.
* `ByteArray.fromUTF8(str: string): ByteArray` - Decomposes UTF8 string into bytes.
* `ByteArray.empty(): ByteArray` - Constructs a `ByteArray` with length of 4 and filled by 0.

_Type conversions_

* `b.toHexString(): string` - Converts to a hex string prefixed with `0x`.
* `b.toString(): string` - Interprets the bytes as a UTF-8 string.
* `b.toBase58(): string` - Encodes the bytes into a base58 string.
* `b.toI32(): i32` - Interprets the bytes as a little-endian `i32`. Throws in case of overflow.
* `b.toI32BigEndian(): i32` - Interprets the byte array as a big-endian `i32`. Throws in case of overflow.
* `b.toU32(): u32` - Interprets the bytes as a little-endian `u32`. Throws in case of overflow.
* `b.toU32BigEndian(): u32` - Interprets the byte array as a big-endian `u32`. Throws in case of overflow.
* `b.toI64(): i64` - Interprets the bytes as a little-endian `i64`. Throws in case of overflow.
* `b.toI64BigEndian(): i64` - Interprets the byte array as a big-endian `i64`. Throws in case of overflow.
* `b.toU64(): u64` - Interprets the bytes as a little-endian `u64`. Throws in case of overflow.
* `b.toU64BigEndian(): u64` - Interprets the byte array as a big-endian `u64`. Throws in case of overflow.

_Operators_

* `b.equals(y: ByteArray): bool` – Can be written as `x == y`, or `eq`.
* `b.notEqual(y: ByteArray): bool` – Can be written as `x != y`, or `ne`.
* `b.concat(other: ByteArray) : ByteArray` - Return a new `ByteArray` consisting of `this` directly followed by `other`
* `b.concatI32(other: i32) : ByteArray` - Return a new `ByteArray` consisting of `this` directly followed by the byte representation of `other`

#### **Bytes**

`import { Bytes } from "@hyperoracle/zkgraph-lib"`

`Bytes` is used to represent arbitrary-length arrays of bytes. This includes Ethereum values of type `bytes`, `bytes32`, etc.

The `Bytes` class extends AssemblyScript's [Uint8Array](https://github.com/AssemblyScript/assemblyscript/blob/3b1852bc376ae799d9ebca888e6413afac7b572f/std/assembly/typedarray.ts#L64) and this supports all the `Uint8Array` functionality, plus the following new methods:

_Construction_

* `Bytes.fromHexString(hex: string) : Bytes` - Converts the string `hex` which must consist of an even number of hexadecimal digits to a `ByteArray`. The string `hex` can optionally start with `0x`.
* `Bytes.fromI32(i: i32) : Bytes` - Converts `i` to an array of bytes.
* `Bytes.fromByteArray(byteArray: ByteArray)` - Converts `ByteArray` to `Bytes`.
* `Bytes.fromU8Array(byteArray: ByteArray)` - Converts `Uint8Array` to `Bytes`.
* `Bytes.fromHexString(hex: string): Bytes` - Input length must be even. Prefixing with `0x` is optional.
* `Bytes.fromUTF8(str: string): Bytes` - Decomposes UTF8 string into bytes.
* `Bytes.empty(): Bytes` - Constructs a `Bytes` with length of 4 and filled by 0.

_Type conversions_

* `b.toHex()` – Returns a hexadecimal string representing the bytes in the array.
* `b.toString()` – Converts the bytes in the array to a string of unicode characters.
* `b.toBase58()` – Turns an Ethereum Bytes value to base58 encoding (used for IPFS hashes).

_Operators_

* `b.concat(other: Bytes) : ByteArray` - Returns new `ByteArray` consisting of `this` directly followed by `other`.
* `b.concatI32(other: i32) : ByteArray` - Returns new `Bytes` consisting of `this` directly follow by the byte representation of `other`.
* `b.slice(start: i32 = 0, end: i32 = this.length): Bytes` - Returns a copy of `b` based on given indices.
* `b.padStart(targetLength: i32, padDigit: u8 = 0): Bytes` - Returns a new `Bytes` with `targetLength` padded by `padDigit` at the front of b.
* `b.padEnd(targetLength: i32, padDigit: u8 = 0): Bytes` - Returns a new `Bytes` with `targetLength` padded by `padDigit` at the end of b.

#### Event

`import { Event } from "@hyperoracle/zkgraph-lib"`

`Event` is used to represent Ethereum event with address, esig, topic, and data as `Bytes`.

_Structure_

```tsx
class Event {
  constructor(
    public address: Bytes,
    public esig: Bytes,
    public topic1: Bytes,
    public topic2: Bytes,
    public topic3: Bytes,
    public data: Bytes,
  ) {}
}
```

#### Require

`import { require } from "@hyperoracle/zkgraph-lib"`

`require` is used to verify inputs and conditions before execution. For instance, if the condition is false, then the require function immediately stops execution.

In the case of zkAutomation, an automation job is triggered as if all conditions in every `require` are true.

To ignore compiler warning in `mapping.ts`, when importing, add `// @ts-ignore` after the import line; when using, write something like `require(true ? 1 : 0)` to convert the boolean to number.

_Syntax_

* `require(condition: i32)` - returns void, and stops execution when condition is false (0).
