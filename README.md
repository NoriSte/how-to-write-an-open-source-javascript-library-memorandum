How to Write an Open Source JavaScript Library - memorandum

This is a memorandum of the evergreen [Kent C. Dodds](https://kentcdodds.com) course about [How to Write an Open Source JavaScript Library](https://egghead.io/courses/how-to-write-an-open-source-javascript-library) available for free on Egghead.
I didn't annotated everything that has been treated in the course. Instead, I annotated just the things that I need to remember compared to what I'd already consolidated 😉

- Add the author and license information
```
npm set-init-author-name 'Stefano Magni'
npm init-author-email 'nori.ste.magni@gmail.com'
npm init-author-url 'https://github.com/NoriSte'
npm set init-license 'MIT'
```

- Save the exact version of the dependencies you install to protect your package from future upgrades of the dependencies themselves.
You can do that with
```
npm install [package] --save-exact
# or with Yarn
yarn add [package] --exact
```

- Use `npm info [package]` to avoid opening the NPM site to check if everything is been published correctly

- To publish a beta version of our package:
  - change the `package.json` version to x.y.x-beta.0
  - `npm publish --tag beta`
  - and now you can install run
  ```
  npm install [package]
  npm install [package]@beta
  # and, if you have added a tag on GitHub, you can install the specific tag too
  npm install [package]@x.y.x-beta.0
  ```

- Install locally `commitizen` and `cz-conventional-changelog`<br>
p.s. Checking on the commitizen site the new way to install them is the following
```
npx commitizen init cz-conventional-changelog --save-dev --save-exact
```
And you can then add some nice npm run scripts in your package.json pointing to the local version of commitizen (if you aren't using husky and precommit):
```json
"scripts": {
  "commit": "npx git-cz"
}
```
And you can add the Citizen badge too
```
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
```
Take a look at the whole [conventionalcommits specs](https://www.conventionalcommits.org) to learn more about it.

Last but not least:

- take a look at the [standard-version library](https://github.com/conventional-changelog/standard-version)
- You can find a long list of badges on [shields.io](https://shields.io)
