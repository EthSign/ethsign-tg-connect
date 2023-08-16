# tg-brother

Proxy tg login site for restricted domain

## Project Setup

```sh
pnpm i

# Compile and Hot-Reload for Development
pnpm dev

# Type-Check, Compile and Minify for Production
pnpm build

# Run Unit Tests with [Vitest](https://vitest.dev/)
pnpm test:unit

# Lint with [ESLint](https://eslint.org/)
pnpm lint
```

## Integration Documentation

1. Configure bot domain to `https://tg-brother.vercel.app/`
2. Use `window.open` open the link `https://tg-brother.vercel.app/?bot_name=<your bot name>`
3. Use `tgBrotherWindow.onmessage` or `tgBrotherWindow.addEventListener('message', handler)` to receive result
