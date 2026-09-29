# Ontologic: the knowledge engine underneath Scadable

Ontologic is the knowledge engine Scadable is building underneath its products. Compliance is its first commercial application.

## What is Ontologic?

Ontologic builds an explicit, provenance-backed model of a company's world from the tools the company already works in, such as Slack, Jira, email and Drive. Instead of treating everything as text for a language model to search, it keeps what exists, what type each thing is, how things relate, and the original evidence behind every claim.

## What is an ontology?

An ontology is a structured representation of a world: the people, companies, systems, documents, events, facts and relationships in it, what type each thing is, how those things relate to one another, and what evidence supports each relationship.

## What does Ontologic keep?

- **Typed entities and relationships:** people, teams, systems, documents, events and how they connect.
- **Records and timelines:** what happened, when, and in what order.
- **Trust levels:** how well supported each fact is, from proposed to verified.
- **Permissions:** who is allowed to see which source, applied to every answer.
- **Exact sets and counts:** computed in code, never estimated by a model.
- **Semantic and lexical indexes** over the original sources.
- **Provenance:** the source, and the exact passage, behind every claim.

## How does Ontologic answer a question?

When a question arrives, Ontologic activates the relevant part of the company's model, retrieves the evidence that bears on it, computes anything that should be computed exactly, and gives the language model a small, high-signal context to reason from. The answer cites its sources. When the evidence does not support an answer, the system says so instead of guessing.

## Why start with compliance?

Compliance exposes exactly the problems Ontologic is designed to solve. A company has to know what happened, who did what, which systems and controls are involved, whether each requirement is met, and, critically, be able to prove every answer from the underlying evidence. Instead of compliance being a pile of forms, screenshots and manual evidence gathering, Scadable can build that understanding continuously from how the company actually operates.

## How reliable is Ontologic today?

The reliability target is intentionally much higher than ordinary retrieval-augmented generation (RAG), so every stage is measured separately rather than hidden behind one aggregate score. On a fresh held-out test of 2,000 documents and 1,416 questions the system had never seen:

| Stage | Literal questions | Paraphrased questions |
| :--- | ---: | ---: |
| All required evidence reached the model | 99.4% | 79.1% |
| Final answer correct | 95.3% | 69.4% |

- **Exact sets and counts:** the dedicated code path produced the exact answer on 60 of 60 fresh questions.
- **Entity and link precision:** roughly 90 to 95%, depending on how chat identities are defined.

Paraphrased questions, where the wording differs from the source, are the current bottleneck, and the part of the system being worked on hardest.

## What is the reliability target?

- About 99% or better availability of the evidence an answer depends on.
- About 99% precision on entities and the links between them.
- 98 to 99% or better precision on trusted structured facts.
- Exact computations, or an explicit statement that the answer is incomplete.
- Eventually, 99.9%-class confidence for any action allowed to happen automatically, and abstention whenever that confidence cannot be established.

Just as important, those numbers must hold as a company's knowledge grows from thousands to hundreds of thousands of documents.

## How do these numbers compare with other systems?

Carefully. Leading search and memory systems report end-to-end benchmark scores roughly in the high 80s to mid 90s, but on different datasets, models, retrieval budgets and scoring methods. Those results are not an industry average and are not directly comparable with the 99.4% evidence measurement above. The defensible claim is not that Ontologic already beats every system. It is that Scadable is engineering toward a stronger reliability contract than ordinary RAG:

1. Know what evidence exists.
2. Know whether enough of it was examined.
3. Compute exact things in code.
4. Preserve provenance for every claim.
5. Expose uncertainty.
6. Refuse to pretend when the answer cannot be established.

## Where is Ontologic going?

Compliance proves the architecture in a domain where trust matters immediately. If Ontologic can reliably maintain a company's organizational state and reason over it, Scadable becomes more than a compliance application: Ontologic becomes the trusted knowledge and reasoning layer companies build their own workflows and applications on.

## Related

- [Vision: the intelligence layer](./vision.md)
- [What Scadable is](./company.md)
- [Frequently asked questions](./faq.md)
