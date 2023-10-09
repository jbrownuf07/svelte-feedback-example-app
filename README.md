# Svelte Feedback Example App

This is an example app that demonstrates how to use Svelte to build a feedback form. 

The code is based off a Traversy Media tutorial on [Svelte Crash Course](https://www.youtube.com/watch?v=uK2RnIzrQ0M), with a few customizations.

## Get started

Install the dependencies...

```bash
cd svelte-feedback-example-app
npm install
```

...then start [Rollup](https://rollupjs.org):

```bash
npm run dev
```

Navigate to [localhost:8080](http://localhost:8080). You should see the Svelte Feedback Example App running.

## Building and running in production mode

To create an optimised version of the app:

```bash
npm run build
```

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).

