---
title: Encoder.ts
nav_order: 4
parent: Modules
---

# Encoder overview

TODO

- optimize encode when all encoders are noop

Added in v3.0.0

---

<h2 class="text-delta">Table of contents</h2>

- [Encoder (interface)](#encoder-interface)
- [URI (type alias)](#uri-type-alias)
- [Int (constant)](#int-constant)
- [URI (constant)](#uri-constant)
- [UnknownArray (constant)](#unknownarray-constant)
- [UnknownRecord (constant)](#unknownrecord-constant)
- [boolean (constant)](#boolean-constant)
- [encoder (constant)](#encoder-constant)
- [id (constant)](#id-constant)
- [number (constant)](#number-constant)
- [string (constant)](#string-constant)
- [array (function)](#array-function)
- [intersection (function)](#intersection-function)
- [lazy (function)](#lazy-function)
- [literals (function)](#literals-function)
- [literalsOr (function)](#literalsor-function)
- [partial (function)](#partial-function)
- [record (function)](#record-function)
- [refinement (function)](#refinement-function)
- [tuple (function)](#tuple-function)
- [type (function)](#type-function)
- [contramap (export)](#contramap-export)

---

# Encoder (interface)

**Signature**

```ts
export interface Encoder<A> {
  readonly encode: (a: A) => unknown
}
```

Added in v3.0.0

# URI (type alias)

**Signature**

```ts
export type URI = typeof URI
```

Added in v3.0.0

# Int (constant)

**Signature**

```ts
export const Int: Encoder<S.Int> = ...
```

Added in v3.0.0

# URI (constant)

**Signature**

```ts
export const URI: "Encoder" = ...
```

Added in v3.0.0

# UnknownArray (constant)

**Signature**

```ts
export const UnknownArray: Encoder<Array<unknown>> = ...
```

Added in v3.0.0

# UnknownRecord (constant)

**Signature**

```ts
export const UnknownRecord: Encoder<Record<string, unknown>> = ...
```

Added in v3.0.0

# boolean (constant)

**Signature**

```ts
export const boolean: Encoder<boolean> = ...
```

Added in v3.0.0

# encoder (constant)

**Signature**

```ts
export const encoder: Contravariant1<URI> & S.Schemable<URI> = ...
```

Added in v3.0.0

# id (constant)

**Signature**

```ts
export const id: Encoder<unknown> = ...
```

Added in v3.0.0

# number (constant)

**Signature**

```ts
export const number: Encoder<number> = ...
```

Added in v3.0.0

# string (constant)

**Signature**

```ts
export const string: Encoder<string> = ...
```

Added in v3.0.0

# array (function)

**Signature**

```ts
export function array<A>(encoder: Encoder<A>): Encoder<Array<A>> { ... }
```

Added in v3.0.0

# intersection (function)

**Signature**

```ts
export function intersection<A, B, C, D, E>(
  encoders: [Encoder<A>, Encoder<B>, Encoder<C>, Encoder<D>, Encoder<E>]
): Encoder<A & B & C & D & E>
export function intersection<A, B, C, D>(
  encoders: [Encoder<A>, Encoder<B>, Encoder<C>, Encoder<D>]
): Encoder<A & B & C & D>
export function intersection<A, B, C>(encoders: [Encoder<A>, Encoder<B>, Encoder<C>]): Encoder<A & B & C>
export function intersection<A, B>(encoders: [Encoder<A>, Encoder<B>]): Encoder<A & B> { ... }
```

Added in v3.0.0

# lazy (function)

**Signature**

```ts
export function lazy<A>(f: () => Encoder<A>): Encoder<A> { ... }
```

Added in v3.0.0

# literals (function)

**Signature**

```ts
export function literals<A extends S.Literal>(_as: NonEmptyArray<A>): Encoder<A> { ... }
```

Added in v3.0.0

# literalsOr (function)

**Signature**

```ts
export function literalsOr<A extends S.Literal, B>(as: NonEmptyArray<A>, encoder: Encoder<B>): Encoder<A | B> { ... }
```

Added in v3.0.0

# partial (function)

**Signature**

```ts
export function partial<A>(encoders: { [K in keyof A]: Encoder<A[K]> }): Encoder<Partial<A>> { ... }
```

Added in v3.0.0

# record (function)

**Signature**

```ts
export function record<A>(encoder: Encoder<A>): Encoder<Record<string, A>> { ... }
```

Added in v3.0.0

# refinement (function)

**Signature**

```ts
export function refinement<A, B extends A>(_encoder: Encoder<A>, _refinement: Refinement<A, B>): Encoder<B> { ... }
```

Added in v3.0.0

# tuple (function)

**Signature**

```ts
export function tuple<A, B, C, D, E>(
  encoders: [Encoder<A>, Encoder<B>, Encoder<C>, Encoder<D>, Encoder<E>]
): Encoder<[A, B, C, D, E]>
export function tuple<A, B, C, D>(encoders: [Encoder<A>, Encoder<B>, Encoder<C>, Encoder<D>]): Encoder<[A, B, C, D]>
export function tuple<A, B, C>(encoders: [Encoder<A>, Encoder<B>, Encoder<C>]): Encoder<[A, B, C]>
export function tuple<A, B>(encoders: [Encoder<A>, Encoder<B>]): Encoder<[A, B]>
export function tuple<A>(encoders: [Encoder<A>]): Encoder<[A]> { ... }
```

Added in v3.0.0

# type (function)

**Signature**

```ts
export function type<A>(encoders: { [K in keyof A]: Encoder<A[K]> }): Encoder<A> { ... }
```

Added in v3.0.0

# contramap (export)

**Signature**

```ts
<A, B>(f: (b: B) => A) => (fa: Encoder<A>) => Encoder<B>
```

Added in v3.0.0