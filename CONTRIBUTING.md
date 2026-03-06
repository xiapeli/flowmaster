# Contributing to FlowMaster

Thanks for your interest in improving FlowMaster.

## How to Contribute

### Report Issues

Open a [GitHub issue](https://github.com/xiapeli/flowmaster/issues) with:

- What you expected to happen
- What actually happened
- Steps to reproduce
- Your environment (OS, Node.js version, Claude Code version)

### Submit Changes

1. Fork the repository
2. Create a feature branch (`git checkout -b feat/my-change`)
3. Make your changes
4. Test the skill by copying `flowmaster.md` to `~/.claude/commands/` and running `/flowmaster analyze` on a real project
5. Commit with a clear message (`git commit -m "feat: add Flutter deep link detection"`)
6. Push and open a pull request

### Commit Messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add new feature
fix: correct a bug
docs: update documentation
refactor: restructure without changing behavior
```

### What to Work On

- Adding detection patterns for new frameworks or platforms
- Improving layout algorithms for edge cases
- Better UX gap detection heuristics
- Documentation and examples

## Code of Conduct

Be respectful, constructive, and collaborative. We are building tools to help developers ship better products.

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
