# Node.js Express Server with TypeScript and Yarn

This document provides a step-by-step guide for setting up an Express.js project using TypeScript and Yarn. It is designed to be clean, scalable, and production-ready.

---

## 1. Initialize the Project

```bash
mkdir express-ts-app
cd express-ts-app
yarn init -y
```

This creates a new project with a `package.json`.

---

## 2. Install Dependencies

```bash
yarn add express
yarn add -D typescript ts-node @types/node @types/express nodemon
```

- `express` → core web framework
- `typescript` → TypeScript compiler
- `ts-node` → run TypeScript files directly
- `@types/node`, `@types/express` → type definitions for Node.js and Express
- `nodemon` → auto-restart server on changes during development

---

## 3. Configure TypeScript

Generate a `tsconfig.json` file:

```bash
npx tsc --init
```

Replace the contents with the following configuration optimized for Node.js + Express:

```json
{
  "compilerOptions": {
    "rootDir": "./src",
    "outDir": "./dist",

    "module": "CommonJS",
    "target": "ES2020",
    "lib": ["ES2020"],
    "types": ["node"],

    "sourceMap": true,
    "declaration": true,
    "declarationMap": true,

    "strict": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,

    "esModuleInterop": true,
    "skipLibCheck": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

If you prefer using ES Modules (`import/export`), set `"module": "NodeNext"` and add `"type": "module"` in `package.json`.

---

## 4. Configure Nodemon

Create a `nodemon.json` file to simplify development server configuration:

```json
{
  "watch": ["src"],
  "ignore": ["src/**/*.spec.ts"],
  "ext": "ts,json",
  "exec": "ts-node ./src/index.ts"
}
```

This ensures that only relevant files are watched and the server restarts on changes.

---

## 5. Define Scripts

Update `package.json` to include the following scripts:

```json
"scripts": {
  "dev": "nodemon",
  "build": "tsc",
  "start": "node dist/index.js"
}
```

- `yarn dev` → run in development with hot reload
- `yarn build` → compile TypeScript into JavaScript in the `dist` directory
- `yarn start` → run compiled production code

---

## 6. Project Structure

Recommended structure:

```
express-ts-app/
│── src/
│   ├── index.ts        # Entry point
│   ├── routes/         # Route definitions
│   ├── controllers/    # Controllers for handling requests
│── dist/               # Compiled JavaScript output
│── tsconfig.json
│── nodemon.json
│── package.json
```

---

## 7. Example Entry File

Create `src/index.ts`:

```ts
import express, { Request, Response } from "express";

const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

app.get("/", (req: Request, res: Response) => {
  res.send("Hello from Express + TypeScript!");
});

app.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
```

---

## 8. Running the Server

Development mode with hot reload:

```bash
yarn dev
```

Compile TypeScript:

```bash
yarn build
```

Run production build:

```bash
yarn start
```

---

## 9. Notes

- Use `"module": "CommonJS"` for simplicity.
- If using `"NodeNext"` for ES Modules, ensure `package.json` contains `"type": "module"`.
- For larger projects, add folders for routes, controllers, services, and middlewares.
- Consider adding `.env` support with [dotenv](https://www.npmjs.com/package/dotenv) for environment variables.
