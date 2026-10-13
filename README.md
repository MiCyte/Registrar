# Registrar

Documentation for the MiCyte registrar's datums: what the registrar sandbox holds, how each
document is shaped, and where an instance reaches it.

The registrar is the instance that answers *who is this msn*. It keeps the **registry** (one
contact card per msn: its local domain, website domain, published signature and contract
endpoint), the entity collections (legal, natural and administrative entities), address
nodes, and one profile per **administrative entity**: Ohio's 88 counties and its cities,
villages and townships, each with its boundary polygon (browsable as maps in
[`administrative/ohio/`](administrative/ohio/)).

## What this repository is, and is not

It organizes and documents those datums. It is **not** how an instance uses them. On the
network, registrar resources are MSS binary payloads served over the MSN protocol, and an
instance reads them that way:

- `<registrar endpoint>/__mss/public/stills/registry.mss` serves the registry still without a contract (for FND: https://micyte.com/__mss/public/stills/registry.mss);
- an instance keeps its own card current by **declaring** it to the registrar
  (`POST <registrar endpoint>/__instance/registry/declaration`), signed with the key its card
  publishes. See *The declaration* in the core's
  [contract formation](https://github.com/MiCyte/MiCyte/blob/main/docs/contracts/contract_formation.md).

A file here is a readable description of a payload, kept beside the payload's shape. It never
replaces the payload.

## Layout

| path | what it documents |
|---|---|
| `registry/` | the contact card: fields, addresses (`rf.3-1-*`), how a declaration updates it |
| `entities/` | legal, natural and administrative entity collections |
| `administrative/` | administrative-entity profiles: identifiers, names, boundary polygons |
| `logs/` | the registrar's local-domain, hierarchy and quality-control logs |

The folders fill as each set is documented. The core software, its versioning and its wiki
are in [MiCyte/MiCyte](https://github.com/MiCyte/MiCyte).

## Licence

AGPL-3.0, the same as the core.
