# Development

This project uses a monorepo structure with the following packages:

- `livesession`: Main API client
- `@livesession/oauth`: OAuth authentication package

## Building

```sh
# Build all packages
npm run build

# Build specific package
cd packages/livesession-node && npm run build
cd packages/oauth && npm run build
```
