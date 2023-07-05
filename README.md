# Migrating to Vite from Create React App

## Why the Need for Migration?

[Create React App (CRA)](https://github.com/facebook/create-react-app) has long been the preferred tool for initiating new React projects. It offers an easy-to-use command-line interface, a development server, automatic transpilation, and many other features that simplify the setup of a React codebase.

However, CRA seems to be facing challenges in terms of its future viability. Over [450 pull requests](https://github.com/facebook/create-react-app/pulls) and [1600 issues](https://github.com/facebook/create-react-app/issues) are open and pending, and there has been a noticeable decrease in recent updates. This stagnation may indicate potential issues with keeping up with the dynamic nature of web development and the evolving needs of developers.

In light of these developments, the React team no longer recommends CRA for new projects as stated in their [official documentation](https://react.dev/learn/start-a-new-react-project#building-with-a-full-featured-framework). Furthermore, Dan Abramov, a member of the React Core team, has shared [insights](https://github.com/reactjs/react.dev/pull/5487#issuecomment-1409720741) into the future plans of CRA, detailing a shift towards becoming a launcher.

Considering these developments, it becomes increasingly clear that developers may need to seek alternatives to CRA that offer advanced features, a customizable development experience, and most importantly, active maintenance.

## Exploring the Alternatives

[Start a New React Project section](https://react.dev/learn/start-a-new-react-project) of official React docs recommends using ready React fullstack frameworks. But in our case we don't need to have fullstack framework.

Here are the most notable alternatives:

- [Next.js](https://nextjs.org/): This full-stack React framework is more than just a tool for building user interfaces; it also allows developers to create APIs. It's maintained by [Vercel](https://vercel.com/), a company that provides easy deployment services for Next.js apps.

- [Remix](https://remix.run/): Another full-stack React framework, Remix offers features like nested routes which can facilitate parallel fetching, providing an enhanced user experience.

- [Vite](https://vitejs.dev/): Although not explicitly recommended in the React docs, Vite is very similar to CRA in that it supports client-side rendering. It offers a simple and efficient setup for developing React projects locally, providing advanced features like Hot Module Replacement (HMR), quick server starts, and native TypeScript support.
  - You can also check this quick overview video [Vite in 100 Seconds](https://youtu.be/KCrXgy8qtjM)

Each of these alternatives offers unique advantages depending on your specific needs. However, in this doc, we will focus on the migration from CRA to Vite. The next sections of this document will delve into detailing the reasons behind our choice and [why we chose Vite](https://vitejs.dev/guide/why.html#why-vite) and the benefits we observed post-migration.

## Why Vite? And The Advantages of Vite in React Development

As we work on increasingly complex applications, traditional JavaScript tools struggle to maintain performance due to the significant increase in JavaScript volume. Starting a development server or reflecting file edits can slow down significantly, impacting the efficiency of the feedback loop and, consequently, developer productivity.

Vite emerges as a superior alternative to CRA in this landscape. Vite's foundation on [esbuild](https://esbuild.github.io/), a JavaScript bundler written in Go, allows for dependency bundling 10-100x times faster than typical JavaScript-based bundlers. This speed boost, coupled with Vite's use of the browser's native [ES Module (ESM)](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/) for on-demand parsing and compiling code, leads to superior performance and faster development times.

Unlike traditional bundler setups that require the dev server to build the entire application before it can be served, Vite optimizes the process by categorizing the application's modules into dependencies and source code. The mostly stable and infrequently changed dependencies are pre-bundled by esbuild, while the source code, which undergoes frequent edits, is served over native ESM as the browser requests it. This innovative approach significantly [improves the development server's start](https://vitejs.dev/guide/why.html#slow-server-start) time and the live-update performance.

Moreover, Vite addresses the [slow updates](https://vitejs.dev/guide/why.html#slow-updates) often associated with traditional bundler setups. Instead of rebuilding the entire bundle upon every file edit, Vite performs Hot Module Replacement (HMR) over native ESM, invalidating only the chain between the edited module and its closest HMR boundary. This ensures consistently fast HMR updates, regardless of the application's size. Vite also accelerates full page reloads using HTTP headers to enforce caching and avoid unnecessary server requests.

Beyond its speed and efficiency, Vite also brings flexibility to development. It supports absolute imports for easier codebase management, environment variables for app configuration based on the running environment, and extensive plugin compatibility.

In summary, Vite offers an advanced, efficient, and customizable React development experience that keeps up with the growing complexity of modern applications. In conclusion, the migration to Vite will provide us with a faster, more efficient development process, significantly improving our productivity and overall experience.

## Conclusion: Embracing Evolution and Progress with Vite

As the React ecosystem continues to evolve, it's evident that the community has made strides in advancing the tools available for building React applications. The progressive decline of Create React App (CRA) simply indicates this natural transition, ushering in a new era of more powerful and efficient alternatives.

One such standout alternative is Vite. Vite offers an enhanced, efficient, and customizable React development experience adept at managing the intricacies of modern applications. The migration to Vite not only accelerates the development process but also significantly amplifies our productivity and user experience.

Alternatives to CRA often provide more advanced features and capabilities that enhance the performance and scalability of React applications, making them a viable choice for production use. A more active and engaged community is another inherent benefit of these alternatives, providing invaluable support and knowledge exchange for developers at all experience levels.

For instance, Next.js boasts a large, active community, with developers contributing their experiences and solutions through various online platforms. This invaluable resource proves extremely beneficial for developers new to React or those seeking help with specific challenges.

In summary, while CRA's prominence may be waning, the React ecosystem thrives. A variety of alternatives, including Vite + React, can deliver an equally good or superior development experience. Regardless of whether you choose Vite, Next.js, or another alternative, you can rest assured that you're employing a tool that is well-supported, actively maintained, and constructed using contemporary best practices.

The bottom line is this: The React community's progression signifies growth, and embracing these advancements—such as migrating to Vite—can lead to tangible improvements in our development process and output.

## Resources

- [Why Vite](https://vitejs.dev/guide/why.htm)
- [Vite Features](https://vitejs.dev/guide/features.html)
- [Create React App is dead! What are the alternatives?](https://www.crocoder.dev/blog/create-react-app-is-dead-what-are-the-alternatives/)
- [CRA is dead. What to use instead?](https://medium.com/@dawid.niegrebecki/create-react-app-is-dead-what-to-use-instead-fcdd46b70295)
- [GitHub PR of official React docs - Replace CRA recommendation with Vite](https://github.com/reactjs/react.dev/pull/5487)
- [GitHub issue of Create React App - CRA is gone from React docs, What happens to it now?](https://github.com/facebook/create-react-app/issues/13072#issuecomment-1475001972)
