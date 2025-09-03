# Express + TypeScript + Yarn Starter

This project demonstrates how to set up a simple backend service using **Node.js**, **Express**, **TypeScript**, and **Yarn**. It is a minimal yet production-ready boilerplate that can be extended for real-world applications.

---

## Features

- [x] TypeScript for type safety
- [x] Express.js as the web framework
- [x] Yarn as the package manager
- [x] Nodemon for development hot reloading
- [x] Clean project structure
- [x] Ready for production builds

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/express-ts-app.git
cd express-ts-app
```

### 2. Install Dependencies

```bash
yarn install
```

### 3. Run in Development

```bash
yarn dev
```

Visit: [http://localhost:3000](http://localhost:3000)

### 4. Build for Production

```bash
yarn build
```

### 5. Start Production Server

```bash
yarn start
```

---

## Project Structure

```
express-ts-app/
│── src/
│   ├── index.ts        # Application entry point
│   ├── routes/         # Define Express routes
│   ├── controllers/    # Business logic for routes
│── dist/               # Compiled JavaScript output
│── tsconfig.json       # TypeScript configuration
│── nodemon.json        # Nodemon configuration
│── package.json
│── .gitignore
```

---

## Example Endpoint

`src/index.ts` includes a sample route:

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

## Scripts

| Command      | Description                                  |
| ------------ | -------------------------------------------- |
| `yarn dev`   | Run in development mode with hot reload      |
| `yarn build` | Compile TypeScript into JavaScript (`dist/`) |
| `yarn start` | Start the compiled production server         |

---

## Requirements

- Node.js (>= 16.x recommended)
- Yarn (>= 1.22.x)
# ts-express-setup
