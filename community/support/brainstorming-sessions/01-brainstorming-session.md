# Brainstorming Session #1

date: 2023-12-14 @ 15:00 UTC
attendees(discord & github username):
- soyboy_vegan, @sbvegan
- hashigo, @hash1go
- tp, @imtipi
- simple8720, @opfocus
- chomtana, @Chomtana
- Billy191, @Billy19191

## Purpose

This session is to understand what training materials would be useful for the TechNERD program.

## Agenda

- Introduction / Purpose / Attendence (~5m)
- Review our current resources (~15m)
- Gather gaps in our knowledge (~15m)
- Training and development we want (~15m)
- Reflect / Conclude (~5m)

## Reflection

Here is the resulting [Figjam Board](./TechNERD%20Brainstorming%20Session%201.png). Our session resulted in a few high level categories that are summarized below.

### Review of current resources

We currently have: 

- [Technical documentation](docs.optimism.io)
- [Developer forum](https://github.com/ethereum-optimism/developers/discussions)
- Discord developer channels

The following are thoughts on how we can improve our current resources:

- Improving the templates on the discussion forum (network they're running, software versions, and the L1 they're targeting)
- Well defined processes for the developer forum
  - How to search closed/answered topics for self service
  - Process around answering, closing, redirecting questions
- A sequential flow of deploying the OP Stack
  - Deploying vanilla OP Stack for basic understanding
  - How to deploy blockscout
  - How to bridge to OP stack and test
  - How to config deploy-config
  - How to config each flag in service
  - How to add second node
  - How to deploy bridge UI
  - How to deploy monitoring stack
  - How to hack OP Stack
- Technical FAQ in the docs

### Gaps in knowledge

The following list are some of the gaps of knowledge that the participants identified:

- A need for foundational knowledge in execution clients, consensus clients, and JSON RPCs
- Foundational knowledge on how the OP Stack components work together
- OP Stack Security
  - Hardware and remote signing support
  - Private key management for deploying an OP Stack Chain
  - Managing private keys
  - Dispute game and fault proof knowledge
- Production sequencer management and failover techniques
- L2 <> L2 interoperability

### TechNERD Training Program

The following are thoughts on how we can improve from the first round training program:

- Foundational knowledge that the TechNERDs need to know
- A layered training approach
  - High level tools to deploy things
  - Sequential tutorial excluding customization and let them deploy things without using high-level tools
  - Provide cusomization document
  - Scenario to solve as an exam
 - Technical workshop beside each topic to deeply understand the fundamentals and how to solve some common issues
 - Training FAQ with perviouisly closed tickets as teaching materials
