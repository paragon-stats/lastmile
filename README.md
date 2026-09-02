# lastmile

A behavioural harness for AI coding agents. It stops the agent deferring the
last mile of work — filing issues instead of finishing adjacent changes,
claiming rules that nothing enforces, and reporting work complete without ever
running the artifact.

> The last mile is the work. Tests passing is not delivery. A tracked issue is
> not a fix.

## The problem it solves

An agent optimises the defensibility of each individual action rather than your
outcome. Widening scope is a named, penalised failure; leaving adjacent finished
work behind is not. So deferral always produces an unassailable sentence —
*"tracked in #241"*, *"deliberately outside this PR"* — and the agent emits
those as if they were features of the report.

You experience the sum, not the individual decisions. The sum is a fragmented
repo, a wrong "done", and a series of round trips where you tell it to finish
what it already started.

The second half is the same root: *"the tests pass"* accepted as proof about a
binary nobody executed.

## Install

```sh
git clone https://github.com/paragon-stats/lastmile
cp -r lastmile ~/.claude/skills/lastmile
```

Claude Code picks it up on the next session. Verify with `/lastmile` or by
asking what skills are loaded.

## What it does

**A gate** that runs before the agent reports work complete or defers anything:

1. Did I run the thing — the artifact, not the tests?
2. Did I claim a rule nothing enforces?
3. Am I about to file adjacent finished work instead of doing it?
4. Am I citing a ticket I created as an external constraint?
5. Would filing cost more than fixing?
6. Am I asserting something I have not opened?

**A bundle test** with an explicit split rule, so "does this belong in this
change?" has an answer rather than an instinct.

**A stop rule** — the counterweight, so finishing never becomes licence to keep
going. Before replacing, rewriting or deleting anything: *was this rewrite the
task, or did it become the task while I worked?* It stops and asks when the
thing already works and the task did not name it, when the change has grown to
rewrite most of an unnamed file, when the decision is the user's to make, or
when it would proceed without evidence it does not have. It never fires on
additive work, mechanical wide-but-shallow changes, or rewrites that **are** the
assignment — and it asks rather than abandons, because downing tools mid-change
produces the very half-finished state the rest of the skill prevents.

**Banned sentences** — the specific phrases that sound responsible and cost you
a turn.

**A self-signal**: instant capitulation means the position was never reasoned,
and a correction that names no mechanism fixes nothing.

## What it is not

It does not license building more. Scope discipline is
[ponytail](https://github.com/DietrichGebert/ponytail)'s job, and where they
disagree, ponytail wins:

> **ponytail governs how much you build. lastmile governs whether you finish
> it.**

lastmile applies only to work already in hand.

## Provenance

Every rule came from a logged failure in real sessions, and each ships with the
evidence that produced it — a rule whose reason has been sanded off is the first
one dropped when it is inconvenient. The headline case: four consecutive
releases shipped a CLI binary with no `--help`, because every test ran in-process
and nothing ever executed the published artifact.

The stop rule was *derived*, not assumed. The starting hypothesis — "push back
above 50% rewritten" — was measured against two repos and rejected: size did not
predict trouble, a >50%-churn filter selected sixteen legitimate
operator-directed retirements and caught none of the real interventions, and
everything actually stopped was stopped at proposal stage, before it was ever a
diff. What the interventions shared was authority and verification, not size.

## Turning it off

`stop lastmile` or `normal mode`. Levels: `/lastmile lite|full|ultra`.

## License

MIT
