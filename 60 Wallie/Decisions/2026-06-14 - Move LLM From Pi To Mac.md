# Move LLM From Pi To Mac

Date: 2026-06-14

## Decision

Local LLM inference will no longer run on the Raspberry Pi.

The Raspberry Pi will focus on infrastructure, storage, automation and future sensor integration.

LLM workloads will run on external hardware when required.

Current target hardware:

- MacBook Pro 8 GB

## Reason

The Raspberry Pi has limited CPU and memory resources.

Running Ollama and local models consumed significant storage and system resources while providing limited performance.

Moving inference to the MacBook provides better performance and keeps Wallie lightweight.

## Consequences

### Positive

- Lower storage usage
- Lower resource consumption
- Simpler maintenance
- Better LLM performance

### Negative

- Local AI depends on the MacBook being available

## Related Decisions

- Oracle VPN migration to Tailscale
- Obsidian selected as knowledge platform
- Markdown selected as canonical knowledge format
