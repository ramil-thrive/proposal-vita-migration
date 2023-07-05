# Migrating to Vite from Create React App

## Why the Need for Migration?

[Create React App (CRA)](https://github.com/facebook/create-react-app) has long been the preferred tool for initiating new React projects. It offers an easy-to-use command-line interface, a development server, automatic transpilation, and many other features that simplify the setup of a React codebase.

However, CRA seems to be facing challenges in terms of its future viability. Over [450 pull requests](https://github.com/facebook/create-react-app/pulls) and [1600 issues](https://github.com/facebook/create-react-app/issues) are open and pending, and there has been a noticeable decrease in recent updates. This stagnation may indicate potential issues with keeping up with the dynamic nature of web development and the evolving needs of developers.

In light of these developments, the React team no longer recommends CRA for new projects as stated in their [official documentation](https://react.dev/learn/start-a-new-react-project#building-with-a-full-featured-framework). Furthermore, Dan Abramov, a member of the React Core team, has shared [insights](https://github.com/reactjs/react.dev/pull/5487#issuecomment-1409720741) into the future plans of CRA, detailing a shift towards becoming a launcher.

Considering these developments, it becomes increasingly clear that we may need to seek alternatives to CRA that offer advanced features, a customizable development experience, and most importantly, active maintenance.

## Exploring the Alternatives

Here are the most notable alternatives:

- [Next.js](https://nextjs.org/): This full-stack React framework is more than just a tool for building user interfaces; it also allows developers to create APIs. It's maintained by [Vercel](https://vercel.com/), a company that provides easy deployment services for Next.js apps.

- [Remix](https://remix.run/): Another full-stack React framework, Remix offers features like nested routes which can facilitate parallel fetching, providing an enhanced user experience.

- [Vite](https://vitejs.dev/): Although not explicitly recommended in the React docs, Vite is very similar to CRA in that it supports client-side rendering. It offers a simple and efficient setup for developing React projects locally, providing advanced features like Hot Module Replacement (HMR), quick server starts, and native TypeScript support.
  - You can also check this quick overview video [Vite in 100 Seconds](https://youtu.be/KCrXgy8qtjM)

Each of these alternatives offers unique advantages depending on your specific needs. [Start a New React Project section](https://react.dev/learn/start-a-new-react-project) of official React docs recommends using full-stack React React frameworks. But in our case we don't need to have full-stack framework. So, in this doc, we will focus on the Vite and how we can migration from CRA to Vite. The next sections of this document will delve into detailing the reasons behind our choice and [why we chose Vite](https://vitejs.dev/guide/why.html#why-vite) and the benefits we observed post-migration.

## Why Vite? And The Advantages of Vite in React Development

As we work on increasingly complex applications, traditional JavaScript tools struggle to maintain performance due to the significant increase in JavaScript volume. Starting a development server or reflecting file edits can slow down significantly, impacting the efficiency of the feedback loop and, consequently, developer productivity.

Vite emerges as a superior alternative to CRA in this topic. Vite's foundation on [esbuild](https://esbuild.github.io/), a JavaScript bundler written in Go, allows for dependency bundling 10-100x times faster than typical JavaScript-based bundlers. This speed boost, coupled with Vite's use of the browser's native [ES Module (ESM)](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/) for on-demand parsing and compiling code, leads to superior performance and faster development times.

Unlike traditional bundler setups that require the dev server to build the entire application before it can be served, Vite optimizes the process by categorizing the application's modules into dependencies and source code. The mostly stable and infrequently changed dependencies are pre-bundled by esbuild, while the source code, which undergoes frequent edits, is served over native ESM as the browser requests it. This approach significantly [improves the development server's start](https://vitejs.dev/guide/why.html#slow-server-start) time and the live-update performance.

Moreover, Vite addresses the [slow updates](https://vitejs.dev/guide/why.html#slow-updates) often associated with traditional bundler setups. Instead of rebuilding the entire bundle upon every file edit, Vite performs Hot Module Replacement (HMR) over native ESM, invalidating only the chain between the edited module and its closest HMR boundary. This ensures consistently fast HMR updates, regardless of the application's size. Vite also accelerates full page reloads using HTTP headers to enforce caching and avoid unnecessary server requests.

Beyond its speed and efficiency, Vite also brings flexibility to development. It supports absolute imports for easier codebase management, environment variables for app configuration based on the running environment, and extensive plugin compatibility.

In summary, Vite offers an advanced, efficient, and customizable React development experience that keeps up with the growing complexity of modern applications. And the migration will provide us with a faster, more efficient development process, significantly improving our productivity and overall experience.

## Stats

<details>
  <summary><a href="https://npmtrends.com/react-scripts-vs-vite">NPM Trends react-scripts (CRA) VS Vite</a></summary>
  <br/>
  <img alt="NPM Trends react-scripts (CRA) VS Vite" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/6f469ecb-5eef-42da-a4f7-67631a98a598" />
</details>

- Thrive CRA:

  - <details>
      <summary><code>pnpm start</code> (≈ 10/14s)</summary>
      <br/>
      It takes approximately between <strong>10-14s</strong> to start the project at it's current state with couple of pages and components.
      <br/>
      <br/>
      <img width="1444" alt="Screenshot 2023-07-04 at 9 46 27 PM" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/6ad3808b-fae5-44da-a045-ebac5f7bd45d">
    </details>
  - <details>
      <summary><code>pnpm build</code> (≈ 18/22s)</summary>
      <br/>
      It takes approximately between <strong>18-22s</strong> to build the project at it's current state with couple of pages and components.
      <br/>
      <br/>
      <img width="1444" alt="Screenshot 2023-07-04 at 9 48 01 PM" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/dd13afa0-786b-4998-a350-4a0c457d91ca">
    </details>

- Thrive Vite:
  - <details>
      <summary><code>pnpm start</code> (≈ 800/500ms)</summary>
      <br/>
      It takes <strong>less than a second</strong> to start the project at it's current state with couple of pages and components. And after each start it gets even faster.
      <br/>
      <br/>
      First try: <img width="1444" alt="Screenshot 2023-07-04 at 9 52 37 PM" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/b4c717ef-5786-4636-a682-aaef307c60ef">
      Second try: <img width="1444" alt="Screenshot 2023-07-04 at 9 52 52 PM" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/96b2ceb9-2ec5-4872-b33b-bdcd9d56888a">
      Third try: <img width="1444" alt="Screenshot 2023-07-04 at 9 52 58 PM" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/d11a7a65-c83a-4340-affe-afb0e6c4d3dc">
    </details>
  - <details>
      <summary><code>pnpm build</code> (≈ 5-7s)</summary>
      <br/>
      It takes approximately between <strong>5-7s</strong> to build the project at it's current state with couple of pages and components.
      <br/>
      <br/>
      <img width="1444" alt="Screenshot 2023-07-04 at 9 53 49 PM" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/8ec075e7-1006-482b-9b71-618262c39c1b">
    </details>

<details>
  <summary>Build size difference for Thrive CRA & Vite (10.2MB vs 1.8MB)</summary>
  <br/>
  Build size reduced from 10.2MB to 1.8MB (≈ 82.35% lighter).
  <br/>
  <br/>
  <img width="1357" alt="Screenshot 2023-07-04 at 10 24 22 PM" src="https://github.com/ramil-thrive/proposal-vita-migration/assets/132285107/ea670846-1779-4521-8741-620d3361176b">
</details>

## Resources

- [Create React App is dead! What are the alternatives?](https://www.crocoder.dev/blog/create-react-app-is-dead-what-are-the-alternatives/)
- [CRA is dead. What to use instead?](https://medium.com/@dawid.niegrebecki/create-react-app-is-dead-what-to-use-instead-fcdd46b70295)
- [GitHub PR of official React docs - Replace CRA recommendation with Vite](https://github.com/reactjs/react.dev/pull/5487)
- [GitHub issue of Create React App - CRA is gone from React docs, What happens to it now?](https://github.com/facebook/create-react-app/issues/13072#issuecomment-1475001972)
- [Why Vite](https://vitejs.dev/guide/why.htm)
- [Vite Features](https://vitejs.dev/guide/features.html)
- [4 Reasons Why You Should Prefer Vite Over CRA](https://semaphoreci.com/blog/vite)
- [Is Vite Really Faster Than Webpack?](https://betterprogramming.pub/is-vite-really-faster-than-webpack-b414f6cc751c)
- [Storybook Performance: Vite vs Webpack](https://storybook.js.org/blog/storybook-performance-from-webpack-to-vite/)
