# Northbridge Data-Structures Architecture Bridge

**Status:** Constructed teaching example; `PLANNED/UNRUN`

**Disclosure:** Northbridge Exchange, its warehouse, records, quantities,
workload, and outcomes are fictional composite teaching material. They are not
production measurements or John Briggs project history.

## The design question

Northbridge wants one partner capability: reserve inventory and advance an
order without promising a result its systems cannot establish. The storage
structure is an implementation choice inside that capability, not the public
contract.

| Need | Working structure | API decision it must not decide by itself |
| --- | --- | --- |
| Find SKU and location | Hash index | Whether the caller may reserve it |
| Preserve order lines and event batches | List/array | Whether list position means business priority |
| Process ordinary work | Deque/FIFO queue | Whether acceptance means completion |
| Process urgent work | Heap/priority queue | Whether urgency overrides authority or fairness |
| Query ordered capacity ranges | Tree or sorted index | Which capacity definition is authoritative |
| Find a picking route | Weighted graph | Whether the route is safe to execute now |

An outgoing order operation still needs identity, authority, transaction
meaning, outcome states, and evidence. A fast dictionary lookup cannot prove a
reservation; a queue cannot prove completion; and a shortest path cannot prove
that a worker or vehicle may take it.

## Plain-language model: the card catalog and the signed claim ticket

A card catalog tells a clerk where an item should be. It does not prove that
the item is still there, that this customer may claim it, or that another clerk
has not already promised it. The API needs both the fast catalog and the
equivalent of a signed claim ticket.

```text
hash lookup -> candidate record -> authority and policy check
            -> conditional reservation write -> durable business outcome
```

A hash lookup may be close to constant time. That makes retrieval efficient;
it does not make the returned state authoritative. If success follows only from
finding and changing the fast view, two callers can be promised the same stock,
a retry can create a second commitment, or an unauthorized caller can reserve
inventory. The lookup can be correct while the transaction is wrong.

## Transfer artifact: capability-versus-structure card

| Decision | Your answer |
| --- | --- |
| Business capability and caller intent | |
| Structure that makes retrieval or selection efficient | |
| Identity, purpose, and authority required | |
| Idempotency and concurrency rule | |
| Durable success, rejection, pending, and unknown outcomes | |
| Evidence that proves which outcome occurred | |
| Revalidation needed if the structure is stale or rebuilt | |

If the structure disappeared tomorrow, could the API still prove who was
authorized, what was committed, and what remains unknown?

## AI-amplified transfer to other systems

AI tools can generate candidate structures, implementation code, tests, and
diagrams for many domains. The architect supplies the governing decisions the
generated machinery must preserve.

| Transfer case | AI can accelerate | Decision the structure cannot settle |
| --- | --- | --- |
| Search-engine indexing | Crawlers, inverted indexes, ranking code, query tests | Content authority, freshness, deletion, ranking policy, and evidence |
| Social-media platforms | Social graphs, feeds, queues, moderation classifiers | Consent, identity, amplification limits, appeal, and causal responsibility |
| Blockchain systems | Transaction parsing, Merkle proofs, graph analysis, contract tests | Signing authority, finality assumptions, off-chain governance, and reversal limits |
| Recommendation systems | Feature pipelines, candidate retrieval, ranking, evaluation | Permitted inputs, objective, fairness, explanation, and user control |
| Online food delivery | Route graphs, order queues, dispatch heaps, ETA models | Order and payment authority, worker custody, retry safety, refunds, and recovery |

The lesson is not that AI removes architecture work. It moves practitioners up
a level: generated machinery arrives sooner, so meaning, authority, failure,
and evidence must become explicit sooner.

> **Why we did not choose every structure**
>
> Autocomplete systems help predict partial search terms, but Northbridge does
> not need that behavior for core inventory and order operations. Huffman
> coding compresses data, but it does not solve lookup, scheduling, routing,
> authorization, or fault tolerance. Choose a structure because the problem
> requires its behavior—not because a course or catalog happens to mention it.
