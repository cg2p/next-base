# next-base

## 1. Create Next App
```
npx create-next-app@latest next-base
cd next-base
yarn dev
```
start a commentary in README.md

create a git repo `next-base` and push first commit
```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/cg2p/next-base.git
git push -u origin main
```

## 2. Create a Custom Document
Create a Custom Document that will update <html> and <body> on all pages ([docs](https://nextjs.org/docs/advanced-features/custom-document))

_document.tsx
```
import { Html, Head, Main, NextScript } from 'next/document'

export default function Document() {
  return (
    <Html>
        <Head>
        <link
            rel="stylesheet"
            href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap"
          />
        </Head>
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  )
}
```
