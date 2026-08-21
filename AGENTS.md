# Documentation project instructions

## About this project

- This is a Mintlify documentation site.
- Pages are MDX files with YAML frontmatter.
- Site configuration lives in `docs.json`.
- Korean and English pages should stay behaviorally aligned when both exist.

## Writing style

- Use active voice and second person.
- Keep sentences concise and focused on one idea.
- Use sentence case for headings.
- Bold UI labels, for example: Click **Settings**.
- Use code formatting for file names, commands, paths, identifiers, and placeholders.
- Minimize unrelated wording, formatting, and metadata changes.

## Customer-specific values

- Write customer-replaceable values as `{UPPER_SNAKE_CASE}`.
- Do not use angle-bracket placeholders such as `<SDK_VERSION>` because MDX may interpret them as tags.
- In shell examples, assign the placeholder first and reference the shell variable afterward:

```bash
SERVER_API_KEY="{SERVER_API_KEY}"

curl -H "x-moment-api-key: ${SERVER_API_KEY}"
```

- Use `Fairy에서 제공한` in Korean and `provided by Fairy` in English when identifying the source of customer-specific values.
- Keep fixed product values, protocol names, supported platform versions, and historical API versions literal unless they vary by customer.

## API key terminology

Use these names consistently:

| Header | Placeholder |
| :-- | :-- |
| `x-moment-api-key` | `{SERVER_API_KEY}` |
| `x-moment-sdk-api-key` | `{SDK_API_KEY}` |

- Do not use generic names such as `{API_KEY}`, `{YOUR_API_KEY}`, or `{PUBLIC_API_KEY}` when the key type is known.

## API request examples

- Show an endpoint as an `http` code block with a relative path.
- Show the base URL separately.
- Show executable requests as `bash` code blocks using `curl`.
- Declare customer-specific and test values at the top of each curl example.
- Use uppercase shell variable names and `${VARIABLE_NAME}` references.
- Show responses as `json` code blocks.
- Omit optional headers such as `accept: */*` unless the endpoint requires them.

Example:

````md
```http
GET /organization/{ORGANIZATION_PUBLIC_ID}/adjustments
```

Base URL: `https://api.public.moment.fairytech.ai`

```bash
ORGANIZATION_PUBLIC_ID="{ORGANIZATION_PUBLIC_ID}"
SERVER_API_KEY="{SERVER_API_KEY}"

curl -X GET \
  "https://api.public.moment.fairytech.ai/organization/${ORGANIZATION_PUBLIC_ID}/adjustments" \
  -H "x-moment-api-key: ${SERVER_API_KEY}"
```
````

## Callouts

- Use `<Tip>` for optional shortcuts or recommendations.
- Use `<Note>` for context required to understand behavior.
- Use `<Warning>` when an incorrect action can cause integration failure, security problems, or data loss.
- Keep recovery or contact guidance as plain text when it applies only to users missing a value.
- Never escape component tags as `\<Tip\>` or `\<aside\>`.

## Validation

Before committing documentation changes, run:

```bash
git diff --check
pnpm dlx mint validate
```
