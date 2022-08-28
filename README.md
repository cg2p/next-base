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

add empty `app.scss` to `styles`. This is where page content styling will be pulled in by `_app.tsx`
update `_app.tsx`
```
import '@/styles/globals.scss';
import '@/styles/app.scss';
```

Reset the global styles, update `global.sccs` with this
```
html {
  box-sizing: border-box;
  font-size: 16px;
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen,
    Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}
body,
h1,
h2,
h3,
h4,
h5,
h6,
p,
ol,
ul {
  margin: 0;
  padding: 0;
  font-weight: normal;
}
h1,
h2,
h3,
h4,
h5,
h6 {
  font-weight: bold;
}

ol,
ul {
  list-style: none;
}

img {
  max-width: 100%;
  height: auto;
}

a {
  color: inherit;
  text-decoration: none;
}
```

## 6. Organise with components
Add in organisation for React components. They all follow this basic structure.
```
--src
    --components
        --Layout
            - Layout.module.scss
            - Layout.tsx
```

`Layout.module.scss`
```
.background {
  background-color: red;
}
```
`Layout.tsx`
```
import React, { ReactNode } from 'react';
import Head from 'next/head';
import styles from './Layout.module.scss';

type Props = {
  children?: ReactNode
  title?: string
}

function Layout({children, title = 'This is the default title' }: Props) {
  return (
    <div className={styles.background}>
      <Head>
      <title>{title}</title>
      <meta charSet="utf-8" />
      <meta name="viewport" content="initial-scale=1.0, width=device-width" />
    </Head>
    {children}
  </div>
  )
};

export default Layout;
```

## 4. Start building basic page scaffold
Create `page/page-1.tsx`
```
import Layout from '@/src/components/Layout/Layout';

const Page1 = () => {
  return (
    <Layout title="Page One">
      <p>page one</p>
  </Layout>
  )
}

export default Page1
```