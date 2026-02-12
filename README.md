# sveltekit-phaser

#### Boilerplate that integrates Phaser 3 into a SvelteKit project.

This project template has been set up using **SvelteKit** and includes:

- _Typescript_
- _Tailwind_
- _ESLint_
- _Prettier_
- _Pre-commit hooks for ESLint and Prettier_
- _Code splitting_

## Build Setup

```bash
# install dependencies
npm install

# serve with live reloading on localhost
npm run dev

# build for production
npm run build

# serve your production build on localhost
npm run preview
```

## Extending the project to your needs

If you want to add more features like _testing_, _i18n_, or a _database_ to
your own project, you can do so quite easily with SvelteKit. Read the
<a href="https://svelte.dev/docs/cli/overview" target="_blank">documentation</a> to get
familiar with the tool and the available add-ons. Also take a look at
<a href="https://github.com/TheComputerM/awesome-svelte" target="_blank">
awesome-svelte</a>.

## Converting into your own repository

If you want to maintain your own repo based on this boilerplate, you first need
to detach it from this repo. Here is what you need to do:

1. Edit these files and enter your own project info
   - _package.json_
   - _README.md_
   - _src/routes/layout.svelte_

2. Delete _LICENSE_ (and perhaps add your own)

3. Reinitialize git
<pre><code>rm -rf .git
git init
git add .
git commit -m "Initial commit"
npm run prepare
</code></pre>

## Sharing data between SvelteKit and Phaser

You might want to expose some game state that lives inside of your Phaser code
to your Svelte components and vice versa, for example a highscore. Here are two
ways you can achieve sharing state between the frameworks.

- Import a Phaser <a href="https://docs.phaser.io/api-documentation/class/events-eventemitter" target="_blank">EventEmitter</a> instance in
  both your Svelte components and Phaser modules. Both sides can then listen to and
  emit events on that emitter.

- Have both sides share a <a href="https://svelte.dev/docs/svelte/stores" target="_blank">
  Svelte store</a> instance. It works like an event emitter, but can also hold
  state. The Svelte store is nicely integrated into your Svelte components and has an accessible API
  that can be used in Phaser code as well.

## Why not use the official template provided by the Phaser team?

The <a href="https://github.com/phaserjs/template-svelte" target="_blank">official Svelte template</a>
works perfectly fine if you prefer to use it. I decided to maintain my own template for the
following reasons:

- The official template only works for building a fully browser rendered SPA. This template also
  works with SRR.
- The Phaser game should be code split from the rest of your UI by default.
- The official template does not cleanly separate Phaser from Svelte code. Svelte components
  should not call Phaser functions and vice versa. Any communication between the two frameworks
  should be handled via EventBus or a shared Svelte store. Not following this principle will result
  in hard to comprehend spaghetti code.
- A template should not contain too much boilerplate or example code that one has to delete.
- Linting, automatic code formatting and Tailwind are a must-have in any of my frontend projects and
  should therefore be included in a template that I want to use myself.
