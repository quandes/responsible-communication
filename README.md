# Responsible Communication

**English** | [Deutsch](README.de.md)

An open agent skill that gives your AI-assisted writing a second voice before publication.
It reads a draft, points to specific passages and asks questions:
Is this claim supported? Is a group being degraded across the board? Does the text describe
a risk, or does it mainly create pressure?

The skill does not decide for you. It discloses its criteria, changes nothing behind your
back, and you can disagree with any of its hints. Sharp criticism may stay sharp.

> **Status: 0.3.0, pilot.** The skill is being tested on real drafts. The test cases in
> this repository describe expected behavior; they have not been independently run
> across models yet. Feedback on false alarms and missed issues is very welcome.

## What it does

- **`reflect` (default):** findings with quote, criterion, observation, evidence status,
  confidence and a reflection question. The text stays unchanged.
- **`review` (on request):** additionally suggests alternative wording that keeps the
  legitimate core of the statement. Nothing is applied automatically.
- **`guardrail` (experimental, not active in 0.2):** a check against a versioned
  organizational policy. Requests fall back to `reflect`.

Criteria: degrading language, unjustified generalization, unsupported facts, misleading
urgency or threat, pressure through guilt or moral belonging, material omissions, privacy
and fabricated authenticity, claimed approvals or availability. See
[`criteria.md`](skills/responsible-communication/references/criteria.md) and the
[disclosed principles](skills/responsible-communication/references/principles.md).

## Example

Draft: *"Anyone who doesn't use our AI will soon be left behind. Responsible teams rely on our solution."*

The skill notes that the first sentence claims a development without evidence, and that
the second ties moral recognition to a purchase decision. It asks: *"Which problem does the
offer demonstrably solve, and how can readers decide for themselves whether it is relevant
to them?"*

## Languages

The skill instructions are in English only, so there is one version to maintain. The
skill reviews drafts in any language, quotes passages in the draft's language and writes
the report in the language of your request, for example German. A German README is
available: [README.de.md](README.de.md).

## Installation

Clone the repository and copy the skill folder into your agent's skills directory.

```bash
git clone https://github.com/quandes/responsible-communication.git

# Claude Code (personal) – or .claude/skills/ inside a project
cp -r responsible-communication/skills/responsible-communication ~/.claude/skills/

# Codex and other Agent Skills hosts – project level
cp -r responsible-communication/skills/responsible-communication .agents/skills/
```

Then ask your agent explicitly, for example:
*"Use responsible-communication to review this draft in reflect mode. Do not change it."*

The skill follows the [Agent Skills specification](https://agentskills.io/specification).
Implicit invocation is disabled for Codex (`agents/openai.yaml`); the review should be a
deliberate choice.

## Limits

- It is a set of instructions for a host agent, not a standalone program. Host rules and
  tools determine what actually runs.
- It is not a legal assessment, a seal of quality or a publishing gate. Approvals must be
  enforced outside the language model.
- A second pass with the same model is not an independent review.
- No protection against disinformation or prompt injection is promised.
- The skill itself stores, logs and transmits nothing. Your host's processing is separate.

## Feedback

Please open an issue with an **anonymized minimal example**: model, skill version,
expected behavior and actual output. Do not paste private drafts or personal details.
Adaptations are welcome; please mark your own rules as such (see
[principles](skills/responsible-communication/references/principles.md#adaptations)).
A fork is not an endorsement by the original authors.

## Background

The skill grew out of the editorial project *KI mit Verantwortung* (AI with
responsibility): AI supports, people remain responsible. Initiated by Matthias Klinger,
maintained by [Quandes](https://quandes.com).

## License

[MIT](LICENSE)
