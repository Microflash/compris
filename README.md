# compris

[![Regression tests](https://github.com/Microflash/compris/actions/workflows/regression.yml/badge.svg)](https://github.com/Microflash/compris/actions/workflows/regression.yml)

A [Vale](https://vale.sh)-compatible prose style for non-native English speakers. Tailored for technical documentation.

## Status: alpha

**compris** is still in its early stages. It is usable but expect massive and frequent changes before it becomes stable.

## Usage

Add <https://github.com/Microflash/compris/releases/download/latest/compris.zip> to the list of `Packages` in the `.vale.ini` file.

```ini
StylesPath = .github/styles
MinAlertLevel = suggestion

Packages = proselint, \
https://github.com/Microflash/compris/releases/download/latest/compris.zip

[README.md]
BasedOnStyles = Vale, compris, proselint
```

To sync the latest updates, run `vale sync`.

## Guiding principles

- Use short sentences (< 30 words).
- Use active voice in simple present tense.
- Avoid Latin to prevent a yet another language in the mix. Use English equivalents. 
- Use an apostrophe only to indicate a possessive.
- Avoid contractions.

## Development

- [Rules](./compris/) are written in `yml` files using the syntax described by [Vale docs](https://vale.sh/docs/).
- Every rule has a [fixture](./fixtures/) against which you can run tests.
- Tests are run against the [log output](./test/expectations/) of Vale.

### Prerequisites

- [Vale](https://vale.sh/docs/vale-cli/installation/)
- [Node.js](https://nodejs.org/en/download)
- [pnpm](https://pnpm.io/installation)

Run `pnpm i` to download the test dependencies; you would need them to run the tests.

### Development workflow

A typical workflow looks like this.

1. Add a new rule by creating a new `compris/<RuleName>.yml` file, or modify an existing rule in the existing `compris/<RuleName>.yml` file.
2. Add or update the fixtures in the `fixtures/<RuleName>/test.md` directory.
3. Add the expected logs in the `test/expectations/<RuleName>.log` file.
4. Run `pnpm test` to run the tests.

## License

[MIT](./LICENSE.md)
