# ADR 057: RPC

## Changelog

- 19-05-2020: created

## Context

Currently the RPC layer of Tendermint is using a variant of the JSON-RPC protocol. This ADR is meant to serve as a pro/con list for possible alternatives and JSON-RPC.

There are currently two options being discussed: gRPC & JSON-RPC.

### JSON-RPC:

JSON-RPC is a json based RPC specification. Tendermint has implemented its own variant of JSON-RPC as it is not compatible with the [JSON-RPC 2.0 specification](https://www.jsonrpc.org/specification).

**Pros:**

- Easy to interface with (JSON)

**Cons:**

- Transmitting JSON, which can be slower than other forms of data transmission.
- Tendermint has its own implementation

### gRPC:

gRPC is a high performant RPC framework. It has been battle tested by a large number of users and is heavily relied on and maintained by countless large corporations.

**Pros:**

- Efficient data retrieval for lite clients and other protocols
- Easily implemented in supported languages (Go, Dart, JS, TS, rust, Elixir, Haskell, ...)
- Efficient data retrieval for users
- Can provide a REST API via [gRPC-gateway](https://github.com/grpc-ecosystem/grpc-gateway)
- Can provide a GraphQL API via [Rejoiner](https://github.com/google/rejoiner)
- HTTP/2-based protocol
- Cacheing, rate limiting, Authentication
- Defined Schema (Protocol Buffers)
- Bi-directional streaming
- When Tendermint-rs begins RPC implementation they will be able to generate a compatible client.

**Cons:**

- Browser support is practically non-existent
- needs a plugin to provide REST API

## Decision

> This section explains all of the details of the proposed solution, including implementation details.
> It should also describe affects / corollary items that may need to be changed as a part of this.
> If the proposed change will be large, please also indicate a way to do the change to maximize ease of review.
> (e.g. the optimal split of things to do between separate PR's)

## Status

> A decision may be "proposed" if it hasn't been agreed upon yet, or "accepted" once it is agreed upon. If a later ADR changes or reverses a decision, it may be marked as "deprecated" or "superseded" with a reference to its replacement.

{Deprecated|Proposed|Accepted}

## Consequences

> This section describes the consequences, after applying the decision. All consequences should be summarized here, not just the "positive" ones.

### Positive

### Negative

### Neutral

## References

> Are there any relevant PR comments, issues that led up to this, or articles referenced for why we made the given design choice? If so link them here!

- {reference link}