# nl-deal-checker

A Claude skill that checks whether a Dutch online deal is real before you buy.

It catches the common traps:

- **Comparison-site prices** that no shop actually charges
- **Marketplace sellers** hiding behind a big shop's name (bol "Verkoop door", Amazon third parties)
- **Contract deals** where the "discounted" phone only exists with a 2-year plan
- **Open-box listings** with hidden damage ("krassen op het scherm")
- **Inflated "was" prices** and cashback rules that exclude your model

## Example

> "Odido has the iPhone for €1,403, bol has it for €1,529. Which is cheaper?"

The skill works out the 24-month total for both, including the plan, and tells you the break-even monthly price.

## Install

**Claude Code**

```bash
mkdir -p ~/.claude/skills/nl-deal-checker
curl -L https://raw.githubusercontent.com/madhav-de/nl-deal-checker/main/SKILL.md \
  -o ~/.claude/skills/nl-deal-checker/SKILL.md
```

**Claude apps**

Download this folder as a zip and upload it as a skill in Claude's settings.

## Use

Just ask Claude about a deal:

- "Is this Coolblue tweedekans TV worth it?" (paste the listing)
- "Should I renew with my provider for the new phone or buy it outright?"
- "Is €1,199 for this TV actually a good price?"

## Contributing

Shops, rules and promotions change. Pull requests with corrections or new traps are welcome.

## License

MIT
