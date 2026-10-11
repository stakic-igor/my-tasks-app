# My Tasks

A lightweight task manager built with Vue 3, TypeScript, and Tailwind CSS. Create tasks, track your progress, and keep your list saved in your browser.

## Features

- Add tasks with a required title and description.
- Mark tasks as completed or active, and delete tasks.
- Filter the list by all, active, or completed tasks.
- View active and completed task counts.
- See filter-specific messages when there are no matching tasks.
- Set a display name for a personalized greeting.
- Keep tasks and your display name between visits using local storage.

## Tech Stack

- Vue 3 with the Composition API and single-file components
- TypeScript
- Vite
- Tailwind CSS 4
- ESLint, Oxlint, and Prettier

## Getting Started

### Requirements

- Node.js matching `^22.18.0 || >=24.12.0`
- npm

### Installation

Run these commands from the project directory:

```sh
npm install
npm run dev
```

Open the local URL printed by Vite in your browser.

## Usage

1. Use the add-task icon to open the task form.
2. Enter a title and description, then select **Add task**.
3. Use the task controls to toggle completion or delete a task.
4. Switch between **All**, **Active**, and **Completed** to filter your list.
5. Use the edit icon beside the greeting to set your display name.

## Scripts

| Command              | Description                                   |
| -------------------- | --------------------------------------------- |
| `npm run dev`        | Start the development server with hot reload. |
| `npm run type-check` | Check TypeScript and Vue component types.     |
| `npm run build`      | Run type checking and build for production.   |
| `npm run build-only` | Build for production without type checking.   |
| `npm run preview`    | Serve the production build locally.           |
| `npm run lint`       | Run Oxlint and ESLint with automatic fixes.   |
| `npm run format`     | Format files in `src/` with Prettier.         |

Linting and formatting can modify source files.

### Production Build

```sh
npm run build
npm run preview
```

The production files are generated in `dist/`. The preview server is for checking the build locally, not production hosting.

## Project Structure

```text
src/
  assets/       Shared styles
  components/   Task forms, list items, filters, and statistics
  icons/        SVG icon components
  types/        Task and filter TypeScript types
  views/        Main task view and state management
  App.vue       Root component
  main.ts       Application entry point
public/         Static assets
```

## Data Storage

Tasks are stored under the `tasks` local storage key, and the display name is stored under `name`. Data stays in the browser and origin where it was created; there is no backend, account system, or cross-device synchronization.

Clearing the site's browser storage removes saved tasks and the display name. Avoid storing sensitive information in task descriptions.

## Recommended Editor

Use [VS Code](https://code.visualstudio.com/) with the [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) extension for Vue and TypeScript support.
