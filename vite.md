# React + Vite Setup Guide

This guide provides step-by-step instructions to set up a React project using Vite.

## Prerequisites
Ensure you have the following installed:
- [Node.js](https://nodejs.org/) (Latest LTS recommended)
- [npm](https://www.npmjs.com/) or [pnpm](https://pnpm.io/) or [yarn](https://yarnpkg.com/)

## Step 1: Create a Vite Project
Run the following command to create a new React project using Vite:

```sh
# Using npm
npm create vite@latest my-react-app --template react

# Using yarn
yarn create vite@latest my-react-app --template react

# Using pnpm
pnpm create vite@latest my-react-app --template react
```

Replace `my-react-app` with your desired project name.

## Step 2: Navigate to the Project Folder
```sh
cd my-react-app
```

## Step 3: Install Dependencies
```sh
# Using npm
npm install

# Using yarn
yarn install

# Using pnpm
pnpm install
```

## Step 4: Start the Development Server
```sh
# Using npm
npm run dev

# Using yarn
yarn dev

# Using pnpm
pnpm dev
```

This will start a local development server, usually available at `http://localhost:5173/`.

## Step 5: Build for Production
To generate an optimized production build, run:
```sh
npm run build
```

## Step 6: Preview the Production Build
To preview the production build locally:
```sh
npm run preview
```

## Project Structure
```
my-react-app/
├── node_modules/
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── .gitignore
├── index.html
├── package.json
├── README.md
├── vite.config.js
└── tsconfig.json (if using TypeScript)
```

## Additional Configuration
- To use TypeScript, create the project with:
  ```sh
  npm create vite@latest my-react-app --template react-ts
  ```
- To install additional packages, use:
  ```sh
  npm install package-name
  ```

## Useful Commands
| Command           | Description |
|------------------|-------------|
| `npm run dev`    | Start the development server |
| `npm run build`  | Build for production |
| `npm run preview` | Preview production build |
| `npm run lint`   | Run ESLint checks (if configured) |

## Conclusion
You have successfully set up a React project using Vite! 🚀 Happy coding!
