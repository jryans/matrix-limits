# Matrix Limits

A collection of various limits and related factoids about the Matrix
specification and implementations.

## Contents

- [Specification](#specification)
  - [Events](#events)
  - [Identifiers](#identifiers)
- [Servers](#servers)
  - [Synapse](#synapse)
  - [Dendrite](#dendrite)

---

## Specification

### Events

The content has been adapted from [the
spec](https://spec.matrix.org/unstable/client-server-api/#size-limit) itself.

- Events must not be larger than 64 KiB when [formatted as a
  PDU](https://spec.matrix.org/unstable/server-server-api/#pdus)
- `sender` must not exceed 255 bytes (including domain)
- `room_id` must not exceed 255 bytes
- `state_key` must not exceed 255 bytes
- `type` must not exceed 255 bytes
- `event_id` must not exceed 255 bytes

### Identifiers

- [User ID
  localparts](https://spec.matrix.org/unstable/appendices/#user-identifiers) are
  limited to `[a-z0-9-.=_/]+` in the spec, but historical user IDs can contain
  any printable ASCII except spaces and federation allows arbitrary unicode
  including unprintable ASCII

## Servers

### Synapse

- Events table [used to use a 32-bit stream ordering
  ID](https://github.com/matrix-org/synapse/issues/8255), limiting a server to a
  total of 2^31 (2,147,483,648) events across all known rooms (develop [has
  changed](https://github.com/matrix-org/synapse/pull/10264) to `bigint`, so the
  limit will soon become 2^63)

### Dendrite

---

## Contribute

Contributions welcome! 😄 Read the [contribution guidelines](CONTRIBUTING.md)
first.

## License

Creative Commons Attribution 4.0 International
