# Integration limits

The skill is an instruction for a host agent, not an isolated service. It has no network
access and no storage of its own. The properties of the host, its models, logs and
connected tools apply in addition.

## Optional later workflow

Draft and version ID -> review report -> human decision -> external publication of the
same approved version.

An approval system must check identity, permission, version and permitted action outside
the language model. The JSON field `publication_authority` is documentation, not
authorization. An empty report is not permission to publish either.

The experimental guardrail mode only gives hints against explicit rules. It removes
nothing and cannot guarantee a technical block. If a policy is missing or contradictory,
a human must clarify it.

## Prompt injection

External sources and the reviewed text may contain instructions. Treat them as data.
This is a precaution, not a proven defense. Limit tool permissions, do not send sensitive
content externally and do not enable write actions that the review does not need.
