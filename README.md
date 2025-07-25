# cms-boilerplate-code-Setup

* ✅ Step-by-step instructions
* ✅ All necessary commands & code
* ✅ Project scripts
* ✅ How to add images to the README
* ✅ Notes for developers

---

### ✅ **README.md: Strapi with TypeScript Boilerplate Setup**

```markdown
# 🚀 Strapi + TypeScript Boilerplate Setup

This project sets up a **minimal and clean Strapi CMS** with full **TypeScript** support using **Yarn**.

---

## 📁 Project Structure

```bash
cms-boilerplate/
├── src/
│   ├── api/
│   │   └── example/
│   │       └── controllers/
│   │           └── example.ts
│   └── types/
│       └── strapi.d.ts
├── tsconfig.json
├── package.json
├── .strapi/
└── ...


---

## ⚙️ Tech Stack

- [Strapi](https://strapi.io/) (Headless CMS)
- TypeScript
- Node.js (v18+ recommended)
- Yarn

---
````

## 📦 Installation Guide

### ✅ Step 1: Create the Project

```bash
yarn create strapi-app cms-boilerplate --quickstart --no-run
````


### If you encounter a Node.js version error, please note that Strapi v5 supports only Node.js versions 22 and 20.
To install the latest Strapi, run the following command:


````bash

yarn create strapi cms-boilerplate --quickstart --no-run

````


When prompted:

* ❌ Skip login/signup.

---

### ✅ Step 2: Move Into the Project Directory

```bash
cd cms-boilerplate
```

---

### ✅ Step 3: Add TypeScript Dependencies

```bash
yarn add -D typescript @types/node
```

---

### ✅ Step 4: Create Type Declaration File

📄 `src/types/strapi.d.ts`

```ts
// Basic type declarations for Strapi
declare module '@strapi/strapi' {
  const strapi: {
    (): any;
    start(): Promise<any>;
    stop(): Promise<any>;
  };
  export default strapi;
}

// Minimal admin types to prevent errors
declare module '@strapi/strapi/admin' {
  interface StrapiApp {
    registerPlugin?: (plugin: any) => void;
  }
  export { StrapiApp };
}
```

---

### ✅ Step 5: Configure `tsconfig.json`

📄 `tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "moduleResolution": "node",
    "outDir": "dist",
    "rootDir": ".",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "noImplicitAny": false,
    "resolveJsonModule": true
  },
  "include": ["**/*"],
  "exclude": ["node_modules", "dist", "**/*.test.ts"]
}
```

---

### ✅ Step 6: Update `package.json` Scripts

📄 `package.json`

```json
"scripts": {
  "dev": "concurrently \"tsc -w\" \"strapi develop\"",
  "develop": "strapi develop",
  "start": "strapi start",
  "build": "tsc && strapi build",
  "clean": "rimraf dist"
}
```

Then install the concurrent package:

```bash
yarn add -D concurrently
```
<img width="496" height="412" alt="Img1" src="https://github.com/user-attachments/assets/d644fedb-cab9-43ea-b3f3-6816b2f4d365" />


---

### ✅ Step 7: Create a Minimal TypeScript Controller

###The example.ts was just a scaffolding demo from Strapi's template. 
Real projects should remove unused example files.
Your blog.ts controller already implements all needed methods.

📄 `src/api/example/controllers/example.ts`

```ts
import { Context } from 'koa';

export default {
  async find(ctx: Context) {
    try {
      ctx.body = { message: 'Hello from TypeScript controller!' };
    } catch (err) {
      ctx.body = err;
    }
  },
};
```

---

## 🚀 Run the Project

```bash
yarn dev
```

This runs:

* `tsc -w`: TypeScript in watch mode
* `strapi develop`: Strapi development mode

---


## ✅ Optional: Clean the Build

```bash
yarn clean
```

Removes `dist/` directory.

---

## 🧪 Troubleshooting

| Issue                           | Solution                                                      |
| ------------------------------- | ------------------------------------------------------------- |
| `Cannot find module` errors     | Install missing types: `yarn add -D @types/module-name`       |
| Type errors in controller files | Use `Context` from `koa` or declare type as `any` temporarily |
| Hot-reload not working in WSL   | Set polling: `"usePolling": true` in server config            |

---

## 📚 Learn More

* [Strapi Documentation](https://docs.strapi.io)
* [TypeScript for Strapi](https://docs.strapi.io/dev-docs/typescript)
* [Koa Docs](https://koajs.com/)

---

## 👨‍💻 Author

---  
💻👩‍💻 Built with breaks + bugs 😅 by [Krupa](https://github.com/Krupa2205) 🚀✨


