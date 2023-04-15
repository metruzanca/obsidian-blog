## Step 1 - Setup customize-cra
This allows us to modify babel/webpack configs without ejecting (which gets messy and still being in CRA we get better support)
```bash
npm i react-app-rewired customize-cra
```

## Step 2 - Add the babel plugin
Install the babel plugin
```bash
npm i babel-plugin-styled-components
```

Create a file called `config-overrides.js` in the root of the project

```bash
touch config-overrides.js
```

With the following content
```js
const { override, addBabelPlugins } = require('customize-cra')


if(process.env.NODE_ENV === 'development') {
  module.exports = override(
    addBabelPlugins([
      // Adds the names styled-components to the generated classnames
      // Useful for development
      "babel-plugin-styled-components",
    ])
  )
}
```

### Step 3 - Modify package.json to run customize-cra
Modify all scripts to use `react-app-rewired` instead of `react-app` e.g.
```diff
- "start": "react-app start",
+ "start": "react-app-rewired start",
```