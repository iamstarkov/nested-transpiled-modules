See this discussion https://github.com/postcss/postcss/commit/0945046f2b8022f63409ec056f7e237d38ecc59b

used-lib is transpiling from `src` to `dist`, then it is linking in `app` and is for you to find out how to import `nested/es/folder` from `used-lib`. It turns out that you need `dist` and npm doesn’t respect main or files fields and relying strictly on file system.

```
git clone git@github.com:iamstarkov/nested-transpiled-modules.git
cd nested-transpiled-modules
cd used-lib
npm i
npm link
cd ../app
npm i
npm link used-lib
npm test
```

or in one command:

    git clone git@github.com:iamstarkov/nested-transpiled-modules.git && cd nested-transpiled-modules && cd used-lib && npm i && npm link && cd ../app && npm i && npm link used-lib && npm test

Open `app/test.js` to play around.
