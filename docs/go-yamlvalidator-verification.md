# go-yamlvalidator marketplace verification

Verified at 2026-09-26T22:33:14+00:00. Plugin version: 0.1.0. Library used by the recipes: v1.0.0.
Plugin source commit: fa0191690dce83b0e1e691270d915909f37457ce.

## Package installation and discovery

The candidate marketplace was validated and registered in an isolated Claude
Code configuration directory. Its GitHub source downloaded the published plugin,
not an unpublished local plugin directory.

- Claude Code 2.1.140: marketplace and plugin manifests validated.
- Installation of go-yamlvalidator@easyp-skills succeeded; plugin enabled.
- Component inventory: one skill, no agents, hooks or MCP servers.
- The session initialization advertised go-yamlvalidator:go-yamlvalidator in
  both skills and slash commands.
- All 33 skill files in the installed package matched the source checkout.
- The user's normal plugin configuration was not edited for these checks.

## Executable checks

Packaging, relative-link, frontmatter, fixture and quick-start consistency tests
passed. The full repository Go tests and vet passed with Go 1.24.11. Bundled
recipes passed in a separate module requiring the published v1.0.0, including
race detection; both minimal programs printed valid.

## Agent behavior and generated code

The installed standalone skill was copied without edits into an isolated Codex
workspace. Codex CLI 0.156.1 ran read-only with user configuration disabled,
without network tools or permission to modify the library or marketplace.
Its execution traces show reads of SKILL.md and the relevant bundled references.

One session produced four Go integration functions. A separate test runner, not
the generating agent, tested them against published v1.0.0:

| Generated integration | Independent acceptance cases | Result |
| --- | --- | --- |
| Native name/port schema | Missing/unknown keys, wrong types, null, indentation | Pass |
| Alternative authorization | token or username+password; partial mixtures rejected | Pass |
| Custom JSON Schema key format | Lowercase keys, assertion enabled, arbitrary values | Pass |
| Relative file references | Base file URI, spaces in paths, missing files, root escape | Pass |

The generated code was not manually corrected. All 28 Go test results including
subtests passed, as did race detection and vet.

A second session answered the remaining 15 prompts from the skill's evaluation
rubric. Answers were reviewed against the bundled references and expected
criteria, rather than accepting the agent's own success claim:

| Scenario | Review |
| --- | --- |
| warning-only | Pass |
| nullable-default | Pass |
| json-schema | Pass |
| native-function | Pass |
| keyword-compile | Pass |
| subschemas | Pass |
| content | Pass |
| cache-chain | Pass |
| diagnostic | Pass |
| reader-cancel | Pass |
| cli-native | Pass |
| yaml-bug | Pass |
| older-module | Pass |
| out-of-scope | Pass |
| untrusted-input | Pass |

This covers 19 curated topics in two agent sessions, not 19 independent
statistical trials. Only the four generated integration scenarios above were
additionally checked by independently authored executable acceptance tests.
The exercise is a release smoke test, not an exhaustive behavioral or security
certification.

## Claude Code model-backend limitation

Claude Code installation and discovery succeeded. Its model-answer test could
not complete: the locally configured z.ai backend returned HTTP 429, code 1113,
with an insufficient-balance/no-resource-package message. This backend failure
is not counted as a passing Claude model evaluation. No credentials or account
settings were changed to work around it. Actual skill-guided answers and code
were evaluated through the available Codex client as described above.

## Reproduction

From a library checkout:

~~~bash
claude plugin validate .
go test -count=1 -run '^TestAgentPlugin' .
go test -count=1 ./...
go vet ./...
bash skills/go-yamlvalidator/scripts/check-examples.sh --race
~~~

The skill's evals/scenarios.json contains the behavioral prompts and review
criteria. The verification used the plugin source commit recorded above; later
plugin changes require another check.
