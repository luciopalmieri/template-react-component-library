# Reference

[How to create and publish a react component library](https://dev.to/alexeagleson/how-to-create-and-publish-a-react-component-library-2oe)

# Project Setup

Initialize the project

```bash
npm init -y
```

Install packages

```bash
npm i react typescript tslib @types/react --save-dev
```

# Typescript

Create a default *Typescript configuration fileé

```bash
npx tsc --init
```

and then customize it

```json
{
  "compilerOptions": {
    // Default
    "target": "es5", 
    "esModuleInterop": true, 
    "forceConsistentCasingInFileNames": true,
    "strict": true, 
    "skipLibCheck": true,

    // Added
    "jsx": "react", 
    "module": "ESNext",  
    "declaration": true,
    "declarationDir": "types",
    "sourceMap": true,
    "outDir": "dist",
    "moduleResolution": "node",
    "allowSyntheticDefaultImports": true,
    "emitDeclarationOnly": true,
  }
}
```

- "jsx": "react" -- Transform JSX into React code
- "module": "ESNext" -- Generate modern JS modules for our library
- "declaration": true -- Output a .d.ts file for our library types
- "declarationDir": "types" -- Where to place the .d.ts files
- "sourceMap": true -- Mapping JS code back to its TS file origins for debugging
- "outDir": "dist" -- Directory where the project will be generated
- "moduleResolution": "node" -- Follow node.js rules for finding modules
- "allowSyntheticDefaultImports": true -- Assumes default exports if none are created manually
- "emitDeclarationOnly": true -- Don't generate JS (rollup will do that) only export type declarations

# Rollup

```bash
npm install rollup @rollup/plugin-node-resolve @rollup/plugin-typescript @rollup/plugin-commonjs rollup-plugin-dts --save-dev
```

- @rollup/plugin-node-resolve - Uses the node resolution algorithm for modules
- @rollup/plugin-typescript - Teaches rollup how to process Typescript files
- @rollup/plugin-commonjs - Converts commonjs modules to ES6 modules
- @rollup-plugin-dts - rollup your .d.ts files

# Add rollup.config.js

# Edit package.json

- "main" -- We have defined the output path for commonjs modules
- "module" -- We have defined the output path for es6 modules
- "files" -- We have defined the output directory for our entire library
- "types" -- We have defined the location for our library's types
- "scripts" -- We have defined a new script called rollup. This will run the rollup package with the -c flag which means "use the rollup configuration file". If you're not familiar with script in a package.json file, these are simply shorthand commands you can run by name with npm run {SCRIPTNAME}. So to run this one will be npm run rollup.

# Install and use the new react component library

```bash
npm install @my-github-account/my-cool-component-library
```

```javascript
import MyCustomComponent from '@my-github-account/my-cool-component-library';

const MyApp = () => {
  return (
    <div>
      <MyCustomComponent />
    </div>
  )
}
```

