### Steps:

    git init

    npm init -y

    mkdir src

    npm install -D typescript @types/node

    npx tsc --init

    ts-config.json
    {
     "compilerOptions": {
     "target": "es2016",
     "module": "commonjs",
     "rootDir": "./",
     "resolveJsonModule": true, /* in case you are importing JSON files */
     "outDir": "./build",
     "esModuleInterop": true,
     "forceConsistentCasingInFileNames": true,
     "strict": true,
     "noImplicitAny": true,
     "skipLibCheck": true,
     }
    }

    src/index.ts

    package.json
    "scripts" {
        "build":"tsc"
    }

    npm run build

    package.json
    "scripts" {
        "build":"tsc"
        "start": "node src"
    }

    npm install -D nodemon rimraf npm-run-all ts-node

    package.json
    "scripts": {
        "clean": "rimraf ./build",
        "build": "npm run clean && tsc",
        "start": "node src",
        "local": "ts-node src",
        "local:watch": "nodemon src -e ts,json --exec 'npm run local'",
    }

    npm run local:watch

    npm i -D supertest @types/supertest jest @types/jest ts-jest

    jest.config.js
    module.exports = {
        transform: {
            '^.+\\.ts?$': 'ts-jest',
        },
        testEnvironment: 'node',
        testRegex: './src/.*\\.(test|spec)?\\.(js|ts)$',
        moduleFileExtensions: ['ts', 'js', 'json'],
        roots: ['<rootDir>/src'],
    };

    package.json
    "scripts": {
        "clean": "rimraf ./build",
        "build": "npm run clean && tsc",
        "start": "node src",
        "local": "ts-node src",
        "local:watch": "nodemon src -e ts,json --exec 'npm run local'",
        "test": "jest"
    }

    npm test

    tsconfig.json
    {
        "include": ["src", "package.json"],
        "exclude": ["src/**/*.test.ts"]
    }

    npm install -D @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint prettier eslint-config-prettier

    .eslintrc
    {
        "extends": [
            "eslint:recommended", "plugin:@typescript-eslint/recommended", "prettier"
        ],
        "parser": "@typescript-eslint/parser",
        "plugins": [
            "@typescript-eslint"
        ],
        "root": true
    }

    package.json
    "scripts": {
        "clean": "rimraf ./build",
        "build": "npm-run-all lint format clean && tsc",
        "start": "node src",
        "local": "ts-node src",
        "local:watch": "nodemon src -e ts,json --exec 'npm run local'",
        "lint": "eslint src",
        "format": "npx prettier --write src",
        "format:check": "npx prettier --check src",
        "test": "jest"
    }

### Reference:

- https://medium.com/before-semicolon/how-to-setup-a-typescript-nodejs-server-2023-16f3874f2ce5
