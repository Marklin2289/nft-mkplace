This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.ts`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

## Important changes :

1. Important changes with `<Image>`

If you see some errors related to `<Image>` component

change the import of the Image this way:

```
import Image from 'next/legacy/image'
```

instead of

```
import Image from "next/image"
```

Then it should work the same as in the lectures.

2. Important changes with `<Link>`

If you see this error:

```
Error: Invalid <Link> with <a> child. Please remove <a> or use <Link legacyBehavior>. Learn more: https://nextjs.org/docs/messages/invalid-new-link-with-extra-anchor

This means the <Link> component doesn't need an a element inside anymore.

The fix is very simple. Find in the layout <Link> component, for example, this one:
```

```

<Link
  key={item.name}
  href={item.href}
>
  <a
    className={classNames(
      item.current ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white',
      'px-3 py-2 rounded-md text-sm font-medium'
    )}
    aria-current={item.current ? 'page' : undefined}
  >
    {item.name}
  </a>
</Link>

```

1. And change it to:

```

<Link
  key={item.name}
  href={item.href}
  className={classNames(
      item.current ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white',
      'px-3 py-2 rounded-md text-sm font-medium'
    )}
    aria-current={item.current ? 'page' : undefined}
>
  {item.name}
</Link>


2. OR keep it as it was and add to it legacyBehavior  prop, so it looks like this:



<Link
  key={item.name}
  href={item.href}
  legacyBehavior
>
  <a
    className={classNames(
      item.current ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white',
      'px-3 py-2 rounded-md text-sm font-medium'
    )}
    aria-current={item.current ? 'page' : undefined}
  >
    {item.name}
  </a>
</Link>

```

Very simple. You need to do this with all links. This is the easiest way to fix it and not break the layout.

More ways can be found here:

https://nextjs.org/docs/messages/invalid-new-link-with-extra-anchor

## Update:

- NextJs Image tag :
  `import Image from "next/image";`
  in version 13 change to
  `import Image from "next/legacy/image";`
