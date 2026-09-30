# Nexhub

Nexhub is a GitHub profile explorer for discovering developers, browsing repositories, and comparing public profile stats. It uses GitHub's public REST API and stores favourites and recent searches in your browser..

**Live app:** <https://saurabhhdev.github.io/Nexhub/>

## Features

- Search for GitHub users and revisit recent searches.
- View public profile details and repositories.
- Search, filter repositories by language, and sort by stars, forks, update date, creation date, or name.
- Open repository details and follow links to GitHub.
- Compare two developers by followers, following, and public repository count.
- Save favourite profiles for quick access; favourites persist in local storage.
- Responsive interface with loading and error states.

## Tech stack

- React 19 and Vite
- React Router
- Redux Toolkit and React Redux
- Tailwind CSS 4
- GitHub REST API

## Getting started

Use Node.js 24 (the version used by the deployment workflow) and npm. From this directory, install dependencies and start the development server:

```sh
npm ci
npm run dev
```

Vite prints the local URL in the terminal. Stop the server with `Ctrl+C`.

## Available scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server. |
| `npm run build` | Create the production build in `dist/`. |
| `npm run preview` | Serve the production build locally. Run `npm run build` first. |
| `npm run lint` | Run Oxlint. |

## App routes

| Route | Description |
| --- | --- |
| `/` | Search for a GitHub user and see recent searches. |
| `/user/:username` | View a profile and browse its repositories. |
| `/user/:username/repo/:repoName` | View repository details. |
| `/compare` | Compare two public GitHub profiles. |
| `/favourites` | View and manage saved profiles. |

## Data and API notes

Nexhub requests public user and repository data directly from `api.github.com`; no account or API key is required. GitHub applies rate limits to unauthenticated API requests, so searches may temporarily fail if the limit is reached. Recent searches and favourites are saved in the current browser's local storage and are not synced between devices.

## Deployment

The GitHub Actions workflow in `.github/workflows/deploy.yml` builds the app and deploys the `dist/` directory to GitHub Pages when changes are pushed to `main` (or when manually started). The Vite production base path is configured for the `/Nexhub/` Pages URL.
