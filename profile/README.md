<h1 align="center">SCADABLE</h1>
<p align="center">Building the data and reasoning layer of the future.</p>

<p align="center">
  <a href="https://scadable.com">scadable.com</a> ·
  <a href="https://github.com/scadable/.github/blob/main/docs/ontologic.md">How Ontologic works</a> ·
  <a href="https://github.com/scadable/.github/blob/main/docs/faq.md">FAQ</a> ·
  <a href="https://cal.com/rahbaral/quick-chat">Talk to us</a>
</p>

---

Every company runs on questions it cannot answer quickly. Who can reach production. Which change broke the build last Tuesday. What we promised this customer, and whether we kept it. The answers exist, spread across the tools a company works in every day. Finding them, and proving where they came from, is a search problem.

## Ontologic

An ontology is a structured representation of a world: the people, companies, systems, documents, events and facts in it, what type each thing is, how things relate, and what evidence supports each relationship.

**Ontologic builds that model of a company's world** from the tools it already works in, such as Slack, Jira, email and Drive. Instead of treating everything as text for a language model to search, it keeps:

- **Typed entities and relationships:** people, teams, systems, documents, events and how they connect.
- **Records and timelines:** what happened, when, and in what order.
- **Trust levels and permissions:** how well supported each fact is, and who may see which source.
- **Exact sets and counts,** computed in code, never estimated by a model.
- **Provenance:** the source, and the exact passage, behind every claim.

When a question arrives, Ontologic activates the relevant part of that model, retrieves the evidence, computes anything that should be computed exactly, and hands the language model a small, high-signal context to reason from. The answer cites its sources. When the evidence does not support an answer, it says so instead of guessing.

## How reliable it is

We measure every stage separately instead of hiding behind one score. On a fresh held-out test of 2,000 documents and 1,416 questions the system had never seen:

| Stage | Literal questions | Paraphrased questions |
| :--- | ---: | ---: |
| All required evidence reached the model | 99.4% | 79.1% |
| Final answer correct | 95.3% | 69.4% |

Exact sets and counts were right on 60 of 60 fresh questions. Paraphrased questions are the current bottleneck and where we are working hardest.

**The target:** about 99% or better availability of the evidence an answer depends on, about 99% precision on entities and links, exact computations or an explicit "incomplete", and 99.9%-class confidence before anything happens automatically, holding as a company grows from thousands to hundreds of thousands of documents. We do not claim to beat every system today; other benchmarks use different datasets and scoring. We claim a stronger contract than ordinary retrieval: know what evidence exists, compute exact things in code, preserve provenance, expose uncertainty, and refuse to pretend. [Full numbers and method](https://github.com/scadable/.github/blob/main/docs/ontologic.md).

## Why compliance first

Compliance is the strictest reader a knowledge engine can have. An auditor checks every claim, asks where each answer came from, and does not accept "probably". If our answers hold up in an audit, they hold up anywhere. It is also work companies already need done, so Scadable is the compliance engine that fixes what it finds:

- **Identifies** what does not meet the standard across your code, cloud and identity, once a day.
- **Fixes** it, as a pull request you approve, a setting changed with your sign-off, or a short guide to the one person who has to act.
- **Reports**, with policies written from how your company really works and every result kept as evidence.
- **Certifies**, through an independent audit firm. We prepare everything; the auditor stays independent.

Companies do this to win deals, starting with the SOC 2 report their buyers ask for.

## Where we are going

Compliance proves the architecture where trust matters immediately. If Ontologic can reliably keep a company's state and reason over it, it becomes the trusted data and reasoning layer companies build their own workflows and applications on, for the people and the agents working there.

Read more: [how Ontologic works](https://github.com/scadable/.github/blob/main/docs/ontologic.md) · [our vision](https://github.com/scadable/.github/blob/main/docs/vision.md) · [what Scadable is](https://github.com/scadable/.github/blob/main/docs/company.md) · [FAQ](https://github.com/scadable/.github/blob/main/docs/faq.md)

## What we need

- **Engineers who want the hard version of search.** Retrieval, ranking and extraction where "mostly right" is a failure, and knowing when not to answer is part of the job.
- **Design partners.** Software and AI companies preparing for their first SOC 2 report who want the work done, not a dashboard.
- **Audit firms** who want clients that arrive prepared.

If that is you, [talk to us](https://cal.com/rahbaral/quick-chat).

## Open source

| Repository | What it is |
| :--- | :--- |
| [**ontologichq/kit**](https://github.com/ontologichq/kit) | Ontologic's gRPC API: the contract every client uses to ask questions and import sources. |
| [**ontologichq/cli**](https://github.com/ontologichq/cli) | A command line client for Ontologic. |
| [**sdk**](https://github.com/scadable/sdk) | The `@scadable/*` packages that put a live, maintained legal document (privacy policy, terms) on any site. Our own privacy policy is served through it. |

## Security

To report a vulnerability, see our [security policy](https://github.com/scadable/.github/blob/main/SECURITY.md) or email security@scadable.com.

## Contributors

SCADABLE began as a university course project. The platform has changed a great deal since then, in architecture, market and product, but the original team's work seeded what SCADABLE is today, and they deserve credit for it.

| Full Name | GitHub Username | GitHub Profile |
| :--- | :--- | :--- |
| **Ali Rahbar** | `crypto-a` | [View Profile](https://github.com/crypto-a) |
| **Christopher Li** | `ChristopherLi05` | [View Profile](https://github.com/ChristopherLi05) |
| **Neyl Nasr** | `Lakssito` | [View Profile](https://github.com/Lakssito) |
| **Benjamin Gavriely** | `Benjamin-Uoft` | [View Profile](https://github.com/Benjamin-Uoft) |
| **Matteo Gentili** | `MatteoGentili24` | [View Profile](https://github.com/MatteoGentili24) |
| **Azaria Kelman** | `azariak` | [View Profile](https://github.com/azariak) |
| **Daniel Rafailov** | `danielrafailov1` | [View Profile](https://github.com/danielrafailov1) |

<p align="center">
  <a href="https://scadable.com">scadable.com</a> ·
  <a href="https://github.com/scadable/.github/blob/main/llms.txt">llms.txt</a> ·
  <a href="https://cal.com/rahbaral/quick-chat">Talk to us</a>
</p>
