# EasyP Skills Marketplace

Hub marketplace for Claude Code skill plugins by [EasyP Tech](https://github.com/easyp-tech).

## Install

Add the marketplace once to get access to all EasyP skills:

~~~
/plugin marketplace add easyp-tech/skills
~~~

Then install any skill:

~~~
/plugin install protoc-gen-mcp-skill
/plugin install protobuf-expert-skill
/plugin install go-yamlvalidator@easyp-skills
~~~

## Skills

| Skill | Repository | Description |
|-------|-----------|-------------|
| <code>protoc-gen-mcp-skill</code> | [easyp-tech/protoc-gen-mcp-skill](https://github.com/easyp-tech/protoc-gen-mcp-skill) | Write, generate, and manage MCP servers using protoc-gen-mcp and easyp |
| <code>protobuf-expert-skill</code> | [easyp-tech/protobuf-expert-skill](https://github.com/easyp-tech/protobuf-expert-skill) | Protocol Buffers expert with deep EasyP CLI knowledge |
| <code>go-yamlvalidator</code> | [Yakwilik/go-yamlvalidator](https://github.com/Yakwilik/go-yamlvalidator) | Validate YAML in Go with native schemas, JSON Schema, custom validators, and source-aware diagnostics |

The go-yamlvalidator plugin includes the <code>go-yamlvalidator</code> skill. Invoke it as <code>/go-yamlvalidator:go-yamlvalidator</code>, or ask for help integrating YAML validation in Go.

[go-yamlvalidator verification report](docs/go-yamlvalidator-verification.md) records installation, discovery, executable examples, and agent-behavior checks.
