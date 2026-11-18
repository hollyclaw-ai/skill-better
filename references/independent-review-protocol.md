# Independent Skill Review Protocol

Reusable process for improving an existing skill library with an independent reviewer. Platform-specific numeric caps (description length, curator tools, etc.) come from an explicit adapter; this protocol does **not** invent extra approval gates beyond the roles and live-replace rule below.

## Intended sequence

**Review → suggestions → candidate edits → owner confirmation of candidates → live replace only for confirmed items.**

Within an existing authorization to run this process (or a named batch), the reviewer issues findings and remedies, and the editor **may prepare candidate diffs/branches immediately**. Owner confirmation is for accepting, rejecting, or narrowing those candidates before they replace live packages. Owner may supply evidence when disputing a finding. **Do not** require a separate owner pre-approval merely to *propose* suggestions or to *draft* candidates.

## Roles

| Role | Duty |
| --- | --- |
| **Reviewer** | Independent audit (default read-only against live); findings with path evidence; concrete remedies; must not treat author self-review as settled truth; must not claim owner acceptance for its own drafts |
| **Editor** | Turns remedies into candidate diffs/branches under existing process authorization; does not mark owner acceptance; does not silently replace live |
| **Owner** | Package maintainer; responds to candidates with `accepted` / `rejected` / `partial` + reason when a decision is needed; only owner acceptance (or `partial` within stated bounds) authorizes **live** replace of those items |
| **Final decider** | Human who resolves disagreements that remain after Round 2; not a stand-in for owner silence |

A single agent must **not** play independent Reviewer and then treat its own edited draft as Owner-accepted. Solo maintainer self-audit may still use ordinary audit→apply tooling, but must **not** label that work as an independent third-party review.

## Authority limits

- Owner acceptance of a skill text change does **not** create outbound messaging, publishing, purchasing, credential, or other destructive/irreversible host permissions the governing human never granted.
- Host permission boundaries, privacy rules, and irreversible-action safeguards remain in force unless the host’s own rules and an explicit human grant say otherwise.
- No authorization ⇒ stay read-only (findings and suggested remedies only; no live mutate).
- An explicit grant to produce a **named batch of candidate edits** covers drafting those candidates without re-asking at every micro-stage. It still does **not** by itself replace live packages, and it does not widen host powers.

## Binding

Every review round records:

- Library / platform adapter in force
- Exact ref (commit SHA or immutable snapshot id)
- Package list covered vs explicitly sampled
- Methods used: `static` | `walkthrough` | `model_trigger` | `model_exec` | `not_run`
- Separation of **migration/placement** work from **content governance**

Unknown usage ≠ unused. Missing live copy ≠ reviewed. Repo snapshot ≠ unverified operator-only copy.

## Review dimensions (including burden)

Judge packages on evidence for:

- Trigger fit and sibling collisions
- Instruction density and progressive disclosure
- **Substantive burden:** fewer ineffective steps, waits, repeated confirmations after an in-scope grant already exists, and outdated or over-wide gates — without defaulting to “keep every historical rule,” and without treating deletion of constraints as a success metric by itself
- Preserved task capabilities and host-required safeguards
- Honest evaluation status

Prefer removing superseded duplicate prose and demoting optional detail to references over appending more always-on rules.

## Round 1 (R1)

1. Inventory structure (names, sizes, refs/scripts, inbound links).
2. Sample high-impact packages for substantive review; state sample vs full.
3. Emit findings: severity, evidence path/excerpt, impact, minimal remedy, capabilities to preserve, and burden notes where relevant.
4. Emit ordered suggestions; under existing authorization, editor may attach **candidate diffs** in an isolated workspace or branch.
5. Hand candidates to owner for confirmation. **No live replace** until confirmed.

## Owner response

Supported values per decision unit: `accepted` | `rejected` | `partial` + reason (and bounds if partial).

- No reply ⇒ **pending**, not implied accept.
- Small editorial fixes may share one short response; **do not** force a long per-item form for trivial wording.
- Larger merges, deletes, or gate changes should be decidable as explicit units.
- Disputes: owner may add counter-evidence; reviewer/editor revise the candidate — still no new pre-approval layer before drafting the revision.

## Live apply

- Candidates stay in review workspace or branch until owner confirmation on that item/batch.
- Replace live packages only for `accepted` items (or `partial` within stated bounds).
- Retain a revertible baseline.
- Do not publish private examples into a public skill template as part of optimization.
- Destructive ops (archive/delete/merge that drops unique capability) stay called out and gated by explicit confirmation of those ops.

## Round 2 (R2)

Trigger only on **disputed** items (rejected with unresolved reviewer concern, or `partial` with unresolved bounds).

- Re-review **only** remaining disagreements; do not reopen accepted items.
- Editor may supply a revised candidate; Reviewer re-checks that delta.
- Agreement closes those items immediately — R2 is not mandatory if R1 already aligns.

## Escalation

After R2, list `remaining_disagreements` for the final decider with options, tradeoffs, and a clearly labeled reviewer recommendation (not owner voice). Escalate only unresolved items. Do not speak as the owner.

## Success and honesty

Improvement means better trigger fit, reliable execution, lower substantive burden where evidenced, and preserved required constraints — **not** shorter text alone. Without held-out model evidence, status stays `proposed-unverified` or `applied-unverified`; never claim measured uplift from static review alone.
