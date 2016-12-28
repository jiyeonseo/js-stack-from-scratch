# 밑바닥부터 시작하는 자바스크립트 스택

[![Build Status](https://travis-ci.org/verekia/js-stack-from-scratch.svg?branch=master)](https://travis-ci.org/verekia/js-stack-from-scratch) [![Join the chat at https://gitter.im/js-stack-from-scratch/Lobby](https://badges.gitter.im/js-stack-from-scratch/Lobby.svg)](https://gitter.im/js-stack-from-scratch/Lobby)

[![Yarn](/img/yarn.png)](https://yarnpkg.com/)
[![React](/img/react.png)](https://facebook.github.io/react/)
[![Gulp](/img/gulp.png)](http://gulpjs.com/)
[![Redux](/img/redux.png)](http://redux.js.org/)
[![ESLint](/img/eslint.png)](http://eslint.org/)
[![Webpack](/img/webpack.png)](https://webpack.github.io/)
[![Mocha](/img/mocha.png)](https://mochajs.org/)
[![Chai](/img/chai.png)](http://chaijs.com/)
[![Flow](/img/flow.png)](https://flowtype.org/)

모던 자바스크립트 스택 튜토리얼,**밑바닥부터 시작하는 자바스크립트 스택** 에 오신 것을 환영합니다.

이것은 자바스크립트 스택을 사용하기위한 가장 짧고 빠른 가이드입니다. 이 가이드는 일반적인 프로그래밍 지식과 자바스크립트 기초를 전제로하고 있습니다. 여기서 **도구들을 함께 사용방법**과 각 도구들을 사용하는 **가장 간단한 예제**를 만들어봅니다. 이 튜토리얼을 **스스로 만들어 보는 바닥부터 시작하는 보일러플레이트** 로 볼 수 있습니다.

만약 약간의 JS 인터랙션이 필요한 그냥 단순한 웹 페이지를 만든다면, 여기서 소개하는 모든 스택을 사용할 필요는 없습니다 (ES6 코드를 여러 파일에 쓰고 CLI로 컴파일하고자한다면, Browserify / Webpack + Babel + jQuery 조합으로 충분합니다). 그러나 스케일이 큰 웹 어플리케이션을 만들고자 한다면, 튜토리얼이 첫 시작으로 유용할 것입니다.

이 튜토리얼의 목표는 다양한 도구들의 사용이기 때문에, 도구들의 구조에 대해 자세한 내용은 다루지 않습니다. 좀 더 깊은 내용을 알고 싶다면, 각각의 공식 문서를 참고하거나 다른 튜토리얼을 찾아 보시기 바랍니다.

A big chunk of the stack described in this tutorial uses React. If you are beginning and just want to learn React, [create-react-app](https://github.com/facebookincubator/create-react-app) will get you up and running with a React environment very quickly with a premade configuration. I would for instance recommend this approach to someone who arrives in a team that's using React and needs to catch up with a learning playground. In this tutorial you won't use a premade configuration, because I want you to understand everything that's happening under the hood.

Code examples are available for each chapter, and you can run them all with `yarn && yarn start` or `npm install && npm start`. I recommend writing everything from scratch yourself by following the **step-by-step instructions** of each chapter.

**Every chapter contains the code of previous chapters**, so if you are simply looking for a boilerplate project containing everything, just clone the last chapter and you're good to go.

Note: The order of chapters is not necessarily the most educational. For instance, testing / type checking could have been done before introducing React. It is quite difficult to move chapters around or edit past ones, since I need to apply those changes to every following chapter. If things settle down, I might reorganize the whole thing in a better way.

The code of this tutorial works on Linux, macOS, and Windows.

## Table of contents

[1 - Node, NPM, Yarn, and package.json](/tutorial/1-node-npm-yarn-package-json)

[2 - Installing and using a package](/tutorial/2-packages)

[3 - Setting up ES6 with Babel and Gulp](/tutorial/3-es6-babel-gulp)

[4 - Using the ES6 syntax with a class](/tutorial/4-es6-syntax-class)

[5 - The ES6 modules syntax](/tutorial/5-es6-modules-syntax)

[6 - ESLint](/tutorial/6-eslint)

[7 - Client app with Webpack](/tutorial/7-client-webpack)

[8 - React](/tutorial/8-react)

[9 - Redux](/tutorial/9-redux)

[10 - Immutable JS and Redux Improvements](/tutorial/10-immutable-redux-improvements)

[11 - Testing with Mocha, Chai, and Sinon](/tutorial/11-testing-mocha-chai-sinon)

[12 - Type Checking with Flow](/tutorial/12-flow)

## Coming up next

Production / development environments, Express, React Router, Server-Side Rendering, Styling, Enzyme, Git Hooks.

## Translations

- [中文](https://github.com/pd4d10/js-stack-from-scratch) by [@pd4d10](http://github.com/pd4d10)
- [Italiano](https://github.com/fbertone/js-stack-from-scratch) by [Fabrizio Bertone](https://github.com/fbertone)
- [日本語](https://github.com/takahashim/js-stack-from-scratch) by [@takahashim](https://github.com/takahashim)
- [Русский](https://github.com/UsulPro/js-stack-from-scratch) by [React Theming](https://github.com/sm-react/react-theming)
- [ไทย](https://github.com/MicroBenz/js-stack-from-scratch) by [MicroBenz](https://github.com/MicroBenz)

If you want to add your translation, please read the [translation recommendations](/how-to-translate.md) to get started!

## Credits

Created by [@verekia](https://twitter.com/verekia) – [verekia.com](http://verekia.com/).

License: MIT
