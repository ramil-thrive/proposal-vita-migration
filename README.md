# Proposal for Migrating to Vite from Create React App

## Objective

The objective of this proposal is to recommend a migration from Create React App (CRA) to Vite for our React projects. This is based on several significant developments within the React community and the challenges we are currently experiencing with CRA.

## Problem Statement

CRA has been our tool of choice for initiating new React projects, largely due to its simplicity and easy-to-use command-line interface. However, there are significant concerns regarding the future viability of CRA. This has been highlighted by a substantial number of open and pending [450 pull requests](https://github.com/facebook/create-react-app/pulls) and [1600 issues](https://github.com/facebook/create-react-app/issues), alongside a noticeable decline in recent updates.

Moreover, the React team no longer recommends CRA for new projects, as stated in their [official documentation](https://react.dev/learn/start-a-new-react-project#building-with-a-full-featured-framework). The transition to a launcher, as indicated by Dan Abramov, a member of the React Core team, further raises the need for us to seek a more actively maintained alternative.

## Proposed Solution

After consideration of alternatives such as [Next.js](https://nextjs.org/) and [Remix](https://remix.run/), we propose adopting [Vite](https://vitejs.dev/) as our primary tool for building React projects.

Vite, while not explicitly recommended in the official React documentation, presents several significant advantages:

1. **Performance Improvement**: Built on [esbuild](https://esbuild.github.io/), Vite can bundle dependencies 10-100x faster than typical JavaScript-based bundlers, resulting in faster development times and enhanced developer productivity.
2. **Efficiency in Updates**: Vite optimizes the process of updating code during development by leveraging Hot Module Replacement (HMR) over native ES Module (ESM), ensuring fast and consistent updates.
3. **Flexibility**: Vite supports absolute imports, environment variables, and a wide range of plugins, enabling a more customizable and efficient development process.

## Expected Benefits

1. **Improved Development Times**: As evident in our internal tests, Vite significantly improves the speed of both starting the project and building the project at its current state, outperforming CRA by a wide margin.
2. **Reduced Build Size**: Our internal tests have also indicated a significant reduction in the build size when using Vite compared to CRA, making our application faster and more efficient.
3. **Enhanced Developer Productivity**: By adopting Vite, we can boost the efficiency of our development feedback loop, ultimately leading to enhanced developer productivity and a superior development experience.

## Request for Approval

Requesting approval to initiate the migration process from CRA to Vite. This will involve setting up Vite configurations for our existing projects and updating our development workflow to accommodate this change.

Attached to this proposal are several resources that delve into the reasons behind our choice, [why we chose Vite](https://vitejs.dev/guide/why.html#why-vite), and the benefits we expect to gain post-migration.

Thank you for your consideration.

## Additional Resources

For additional information, please refer to the following resources:

- [Create React App is dead! What are the alternatives?](https://www.crocoder.dev/blog/create-react-app-is-dead-what-are-the-alternatives/)
- [CRA is dead. What to use instead?](https://medium.com/@dawid.niegrebecki/create-react-app-is-dead-what-to-use-instead-fcdd46b70295)
- [GitHub PR of official React docs - Replace CRA recommendation with Vite](https://github.com/reactjs/react.dev/pull/5487)
- [GitHub issue of Create React App - CRA is gone from React docs, What happens to it now?](https://github.com/facebook/create-react-app/issues/13072#issuecomment-1475001972)
- [Why Vite](https://vitejs.dev/guide/why.htm)
- [Vite Features](https://vitejs.dev/guide/features.html)
- [4 Reasons Why You Should Prefer Vite Over CRA](https://semaphoreci.com/blog/vite)
- [Is Vite Really Faster Than Webpack?](https://betterprogramming.pub/is-vite-really-faster-than-webpack-b414f6cc751c)
- [Storybook Performance: Vite vs Webpack](https://storybook.js.org/blog/storybook-performance-from-webpack-to-vite/)
