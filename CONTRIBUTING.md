# Contributing to co-tanstack

Thanks for your interest in contributing!

## Adding a New Command

1. Create a new `.md` file in the `commands/` directory
2. Include the frontmatter block with `description` and `allowed-tools`
3. Follow the existing command structure: identify context, fetch docs, synthesize, enforce rules
4. Submit a PR with a clear description of what the command does and when to use it

## Improving Existing Commands

- Found a missing TanStack topic? Add it to the topic list
- Better prompt wording? Open a PR
- Edge case where the command fails? Open an issue with your session context

## Guidelines

- Keep commands focused on a single concern
- Always ground patterns in official documentation
- Test your command in a real Claude Code session before submitting
