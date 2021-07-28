# WeDancePlatform

> https://wedance.vip/ – community platform for dancers

## Built with

- [Nuxt.js](https://nuxtjs.org) – Vuejs framework, which is used as Static Site Generator.
- [Tailwind CSS](https://tailwindcss.com/) – utility-first CSS framework.
- [Nuxt Composition Api](https://composition-api.nuxtjs.org/) – provides a way to use the Vue 3 Composition API with Nuxt-specific features.
- [Firebase](https://firebase.google.com/) – used as Serverless framework with Firestore realtime database, authentication and cloud functions.
- [Mailgun](https://www.mailgun.com/) – used as an email delivery and tracking service.
- [Sentry](https://sentry.io/) – monitoring platform to log exceptions and errors.
- [Netlify](https://netlify.com/) – CDN, CI and Hosting provider, that deploys site on each commit.

## Installation Guide

### Prerequisites

- [Yarn](https://classic.yarnpkg.com/en/docs/install) – javascript package manager

### Create Firebase project

- Go to [Firebase Console](https://console.firebase.google.com/) click `Add project`, enter any name, click `Continue`, uncheck `Enable Google Analytics for this project`, click `Continue`.
- Under `Get started by adding Firebase to your app` click 3d icon (Web), enter name `Web`, uncheck `Firebase Hosting`, click `Register app`, copy generated `firebaseConfig` for later, you will need it for `.env` file.
- Go to `Authentication`, switch to tab `Sign-in method`, click `Email/Password` and enable both triggers (password and email link); enable `Google`.
- Go to `Cloud Firestore`, click `Create database`, select `Start in test mode`, click `Next`, choose region `eur3`.

### Setup

1. Fork this repository, e.g. https://github.com/we-dance/platform/fork
2. Clone your forked repository with `git clone https://github.com/<your-username>/platform.git`
3. Install dependencies with `yarn install`
4. Set up keys for your local instance of WeDance, you'll need to create an `.env` file. Take a look at `.env.example`. This file lists all the `ENV` variables we use and provides a fake default for any missing keys.
5. Run `yarn dev` to serve site with hot reload at https://localhost:3000/

To activate all services and features see section `Services` below.

### Tools

**Code Editor:** [VSCode](https://code.visualstudio.com/) with following plugins:

- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)

**Browser:** [Chrome](https://chrome.google.com/) with extensions:

- [Vue.js devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)

## Site structure

This site is a [Nuxt.js](https://nuxtjs.org) application. See [Directory Structure](https://nuxtjs.org/guide/directory-structure) and official guide for more information. Also most of folders in this repository has a `README.md` file.

`functions` folder contains Firebase Cloud Functions.

## Deployment Guide

Read [How to deploy on Netlify?](https://nuxtjs.org/faq/netlify-deployment/).

- Push your branch to github.
- Sing in to [Netlify](https://netlify.com/).
- Click `New sity from Git`.
- Choose `GitHub` and select your repository.
- Select your branch.
- Build command: `yarn build`.
- Publish directory: `dist`.
- Click `Advanced build settings` and `New variable`.
- Add all keys and values from `.env` file (`URL` and [some other variables](https://docs.netlify.com/configure-builds/environment-variables/) are set automatically)
- Click `Deploy site`.

To activate all services and features see section `Services` below.

## Services

### Authentication for custom domains

- Go to `Authentication`, switch to tab `Sign-in method` find section `Authorized domains`, click `Add domain` and add new

### City auto-complete

- Enable Maps API in Google API in [Google Cloud Console](https://console.cloud.google.com/apis/library)
- [Enable Billing](https://console.cloud.google.com/project/_/billing/enable) on the Google Cloud Project

### Mailgun

- Create [mailgun](https://www.mailgun.com/) account.
- Create domain and setup DNS.
- Create API key.
- Enable Pub/Sub, Scheduler, Build API in [Google Cloud Console](https://console.cloud.google.com/apis/library).
- Install [Firebase-CLI](https://firebase.google.com/docs/cli) locally and init project with `firebase init`.
- Add mailgun confguration to Firebase:

```bash
firebase functions:config:set mailgun.key="" mailgun.domain="" mailgun.host=""
```

- Deploy Firebase with `firebase deploy`.
- Setup hooks in Mailgun.
- Create firestore index (send test mail, see logs, find link to create index).

## Contributing

We encourage you to contribute to WeDance!

We expect contributors to abide by our underlying [code of conduct](https://wedance.vip/coc). All conversations and discussions on GitHub (issues, pull requests) and across [wedance.vip](https://wedance.vip/) must be respectful and harassment-free.

Remember that communication is the lifeblood of any Open Source project. We are all working on this together, and we are all benefiting from this software. It's very easy to misunderstand one another over asynchronous, text-based conversations: When in doubt, assume everyone within this project has the best intentions.

We are all humans trying to work together to improve the community. Always be kind and appreciate the need for trade-offs. ❤️

### Reporting Issues

A great way to contribute to the project is to send a detailed report when you encounter an issue.

[See issues](https://github.com/we-dance/platform/issues) or [Create an issue](https://github.com/we-dance/platform/issues/new).

#### Bug Report

A good bug report answers the following questions:

- How to reproduce? Steps to reproduce, conditions, environment, browser version.
- What is actual result?
- What is the expected result?

#### Feature request

A good feature request is using the following sentence structure:

As a `Role` I want to `Goal` in order to `Reason`

And include acceptance criteria, which describes a check list with all requirements.

### Where to contribute

Documentation is almost always a great place to start contributing to a new project. WeDance is an Open Source, community-driven project. Therefore, providing and maintaining quality documentation is one of our most important jobs. You can find more information in our docs guide!

Refactoring, which involves improving the code without modifying behavior, is a great place to help out! Generally speaking, you can rely on existing tests to ensure that your refactor doesn't introduce any unexpected behavior. If an area isn't well tested, you might be asked to include a regression test with your refactoring PR. Refactors can touch many files, so we encourage breaking big changes into small PRs.

Fixing bugs is a super fast way to improve the experience for our users! When you're fixing bugs, we appreciate communication in a GitHub issue. If an issue exists, please claim that issue and link it in your PR, otherwise creating an issue is the best first step! Be sure to surround bug fixes with ample tests; bugs are magnets for other bugs. Write tests around bugs!

Building features requires a lot of communication, but we'd love to have your help with this too! Features tend to be subjective and might spur some debate. Be sure to create an issue for new features before getting started! If your feature involves design changes, including design mockups can be very helpful. As always, when in doubt, ask!

### How to contribute

We'd love to see your pull requests, even if it's just to fix a typo!

However, any significant improvement should be associated to an existing feature request or bug report.

#### Getting started

- Setup project locally (see Installation Guide).
- Make changes to code.
- Build and run locally `yarn build && yarn start`.
- Checkout new branch and commit your changes.
- Deploy to Netlify.
- Create a Pull Request and include a link to your Netlify demo.

#### Code Style

##### js, html, vue

As you might have noticed already, we are using ESLint to enforce a code standard. Please run `yarn lint` before committing your changes to verify that the code style is correct. If not, you can use `yarn lint --fix` to fix most of the style changes. If there are still errors left, you must correct them manually.

##### git

We use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/). See examples of [good commits](https://chris.beams.io/posts/git-commit/) and [bad commits](http://whatthecommit.com/).

## The bottom line

We are all humans trying to work together to improve the community. Always be kind and appreciate the need for tradeoffs. ❤️
