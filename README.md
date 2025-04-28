# Official LiveSession TypeScript/JavaScript API Library

[![NPM version](https://img.shields.io/npm/v/livesession.svg)](https://npmjs.org/package/livesession)

This library provides convenient access to the LiveSession API from TypeScript or JavaScript. It includes both the main LiveSession API client and an OAuth package for authentication.

## Installation

```sh
npm install livesession
```

For OAuth functionality:

```sh
npm install @livesession/oauth
```

## Usage

### Main API Client

```typescript
import livesession from 'livesession';

// Initialize with API key from environment variable (LIVESESSION_API_KEY)
const ls = new livesession();

// Or initialize with explicit API key
const ls = new livesession(
  livesession.optionApiKey('your-api-key')
);

// Use the client to make API calls
// Example API calls will be documented here as they are implemented
```

### OAuth Authentication

```typescript
import { OAuth } from '@livesession/oauth';

const oauth = new OAuth(
  {
    clientId: 'your-client-id',
    clientSecret: 'your-client-secret'
  },
  {
    callbackUrl: 'https://your-app.com/callback',
    pkce: true // Enable PKCE for enhanced security
  }
);

// Build authorization URL
const authUrl = await oauth.buildAuthorizeUrl({
  state: 'random-state-string'
});

// Handle OAuth callback
const auth = await oauth.callback(request);
console.log(auth.accessToken);
console.log(auth.refreshToken);

// Get token info
const tokenInfo = await oauth.info(auth.accessToken);
console.log(tokenInfo.userId);
console.log(tokenInfo.accountId);
console.log(tokenInfo.email);

// Refresh token
const newAuth = await oauth.refresh(auth.refreshToken);

// Revoke token
await oauth.revoke(auth.accessToken);
```

## Features

- TypeScript support
- OAuth 2.0 authentication with PKCE support
- Token management (refresh, revoke)
- User information retrieval
- Modern ES modules support
- Tree-shakeable exports

## Requirements

- Node.js 18 LTS or later
- TypeScript 4.6 or later (for TypeScript users)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

