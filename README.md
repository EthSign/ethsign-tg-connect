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
3. Use `window.onmessage` or `window.addEventListener('message', handler)` to receive result

```ts
window.addEventListener('message', (evt) => {
  const { data, origin } = evt
  if (origin === 'https://tg-brother.vercel.app' && data.type === 'tg-brother:telegram_login') {
    // do something
    console.log(data)
  }
})
```

4. Use `?close=1` to auto close window when auth done

[Demo is here](https://tg-brother.vercel.app/demo.html)
