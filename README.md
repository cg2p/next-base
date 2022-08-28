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

## 3. Streamline configuration
Setup `tsconfig.json` to make path coding more streamlined
```
//jsconfig.json
{
  "compilerOptions": {
    ...

    "baseUrl": ".",
    "paths": {
      "@/src/*": ["src/*"]
    }
  }
}
```

## 4. Start building basic page scaffold
Create `page/page-1.tsx`
```
import type { NextPage } from 'next'

const Page1: NextPage = () => {
  return (
    <div>Page 1</div>
  )
}

export default Page1
```

## 5. Switch to Saas styline
Install SaaS
```
yarn add sass@1.51.0
```

Switch to Sass styling. 

In the `styles` folder change `Home.module.css` and `globals.css` to be `.scss` filename.
Update the style import reference in `index.tsx` and `_app.tsx`.

Update `next.config.js` to compile in Sass:
```
/** @type {import('next').NextConfig} */
const path = require('path')

const nextConfig = {
  reactStrictMode: true,
  swcMinify: true,
  sassOptions: {
    includePaths: [path.join(__dirname, 'styles')],
  },
}

module.exports = nextConfig
```



## 6. Organise with components
Add in components

```
--src
    --components
        --Widget

