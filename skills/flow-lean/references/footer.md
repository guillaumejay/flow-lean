# Skills footer

Default `skills-footer=on`. End each final response with exactly one line:

`Skills used: flow-lean, <other-skill>`

- `skills footer on|off|status` toggles it for the current session only.
  `normal mode` changes density, not this setting.
- Keep it for "briefly" or "only the result". Omit it only after
  `skills footer off` or when a machine-enforced output schema forbids extra
  text.
- List a skill only when the root agent loaded its full instructions and
  applied them this turn. Order by first use, deduplicate.
- `flow-lean` counts when its style shaped the response. Write
  `Skills used: none` only when nothing shaped it.
- Exclude router suggestions, availability listings, mentions and
  subagent-only skills.
- The footer is a model declaration, not analytics proof. Native Skill calls
  and loader events remain the exact usage sources.
- No heading, separator, explanation or recap around it.
