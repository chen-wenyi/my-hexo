---
title: How to create React UI Components
tags:
  - UI
categories:
  - React
date: 2021-01-20 15:32:08
---

### Install react app by cra

The reason we init the project by cra is that we can test ui component later.

 <!-- more -->

`npx create-react-app my-ui-component --template typescript`

### Add a folder ‘components’ under project dir

Create an example component called **Button**

Now under the Component dir we have
styles
_ index.less
button
_ index.tsx
index.tsx

### Code in button component

```
// button/index.tsx

import React from ‘react’;
import ‘../style/index.css’;

export const Button: React.FC<{ name: string }> = (props) => <div className=‘my-button’>{props.name}</div>;

export default Button;
```

### Create ts compile configuration file

```
// tsconfig.build.json

{
    “compilerOptions”: {
        “outDir”: “my-fancy-ui”,
        “module”: “esnext”,
        “target”: “es5”,
        “declaration”: “true”, // create .d.ts for each ts file
        “jsx”: “react-jsx”,
        “moduleResolution”: “node”,
        “allowSyntheticDefaultImports”: true,
    },
    “include”:[“components“]
}
```

add script `build:ts tsc -- p tsconfig.build.json`
now we can build ts files to js files.

### But style sheets haven’t been complied to my-fancy-ui

so we need to convert less to css.

firstly we need `npm install -D less`

then we add script `less2css lessc components/style/index.less my-fancy-ui/style/index.css`

combine the scripts to `build:comp npm run build:ts && npm run less2css`

### Build & Test

1. run build:comp
2. move my-fancy-ui to node_modules
3. import Button from my-fancy-ui in App.tsx file under src
4. check if it is work

### Init a new project (npm init)

add below

```
{
  "name": "my-fancy-ui",
  "main": "my-fancy-ui/index.js",
  "module": "my-fancy-ui/index.js",
  "types": "my-fancy-ui/index.d.ts",
  “files”: [
     “my-fancy-ui”
   ],
   “dependencies”: {},
   “peerDependencies”: { // remind user required dependences
      “react”: “>=17.0.1”,
      “react-dom”: “>=17.01”
    }
}
```
