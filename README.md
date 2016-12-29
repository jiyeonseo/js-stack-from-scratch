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

이것은 자바스크립트 스택을 사용하기위한 가장 짧고 빠른 가이드입니다. 이 가이드는 일반적인 프로그래밍 지식과 자바스크립트 기초를 전제로하고 있습니다. 여기서 **도구들을 함께 사용방법**과 각 도구들을 사용하는 **가장 간단한 예제**를 만들어봅니다. 이 튜토리얼을 **스스로 만들어 보는 바닥부터 시작하는 보일러 플레이트** 로 볼 수 있습니다.

만약 약간의 JS 인터랙션이 필요한 그냥 단순한 웹 페이지를 만든다면, 여기서 소개하는 모든 스택을 사용할 필요는 없습니다 (ES6 코드를 여러 파일에 쓰고 CLI로 컴파일하고자한다면, Browserify / Webpack + Babel + jQuery 조합으로 충분합니다). 그러나 스케일이 큰 웹 어플리케이션을 만들고자 한다면, 튜토리얼이 첫 시작으로 유용할 것입니다.

이 튜토리얼의 목표는 다양한 도구들의 사용이기 때문에, 도구들의 구조에 대해 자세한 내용은 다루지 않습니다. 좀 더 깊은 내용을 알고 싶다면, 각각의 공식 문서를 참고하거나 다른 튜토리얼을 찾아 보시기 바랍니다.

이 튜토리얼에서 설명하고있는 스택은 대부분 React를 사용하고 있습니다. 만약 React를 막 시작하고 계신 분이시거나, React에 대해서만 배우고 싶은 경우 [create-react-app](https://github.com/facebookincubator/create-react-app)를 이용해 미리 설정된 React 환경으로 빠르게 실행해 볼 수 있습니다. 예를 들어 이미 React을 사용하는 팀에 합류하여 빠르게 따라잡아야 하는 경우 이러한 접근 방식을 권장합니다. 이 튜토리얼에서는 내부에서 어떤일이 어떻게 돌아가고 있는지 이해하기 위해, 기존의 미리 설정된 값을 사용하지 않을 것 입니다.

코드 예제는 각 챕터마다 유효합니다. 각각 `yarn && yarn start` 또는 `npm install && npm start` 를 이용해 실행할 수 있습니다. 각 챕터들의 *단계별 설명* 에 따라 바닥부터 따라 해 보는 것을 권장합니다.

*모든 챕터에는 이전 챕터까지의 코드가 포함되어 있습니다.* 따라서 모든 것을 포함한 프로젝트의 보일러 플레이트를 찾고 있다면, 마지막 챕터를 clone하면 바로 사용 할 수 있습니다.

주의 : 챕터 순서가 반드시 지켜져야 가장 효율적인 것은 아닙니다. 예를 들어, 테스트 / 타입 체크는 React를 시작하기 전도 할 수 있습니다. 그러나 챕터를 이동 시키거나, 이전 챕터을 수정하는 것은 다음 챕터을 모두 변경해야하기 때문에 상당히 어렵습니다. 나중에 여력이 생긴다면, 더 나은 방법을 찾아 재정렬 해보도록 하겠습니다.

이 튜토리얼의 코드는 Linux, macOS, Windows 환경 에서 동작합니다.

## 목차
[1 - Node와 NPM, Yarn, 그리고 package.json](/tutorial/1-node-npm-yarn-package-json)

[2 - 패키지의 설치 및 사용](/tutorial/2-packages)

[3 - Babel과 Gulp를 이용한 ES6 설치](/tutorial/3-es6-babel-gulp)

[4 - class를 이용한 ES6 문법 사용](/tutorial/4-es6-syntax-class)

[5 - ES6 모듈 문법](/tutorial/5-es6-modules-syntax)

[6 - ESLint](/tutorial/6-eslint)

[7 - Webpack을 이용한 클라이언트 앱](/tutorial/7-client-webpack)

[8 - React](/tutorial/8-react)

[9 - Redux](/tutorial/9-redux)

[10 - Immutable JS와 Redux 개선](/tutorial/10-immutable-redux-improvements)

[11 - Mocha와 Chai, Sinon를 이용한 테스트](/tutorial/11-testing-mocha-chai-sinon)

[12 - Flow를 이용한 타입 체크](/tutorial/12-flow)

## 다음 할 일

실전 / 개발 환경, Express, React Router, 서버 사이드 렌더링, Styling, Enzyme, Git Hooks.

## 번역

- [中文](https://github.com/pd4d10/js-stack-from-scratch) by [@pd4d10](http://github.com/pd4d10)
- [Italiano](https://github.com/fbertone/js-stack-from-scratch) by [Fabrizio Bertone](https://github.com/fbertone)
- [日本語](https://github.com/takahashim/js-stack-from-scratch) by [@takahashim](https://github.com/takahashim)
- [Русский](https://github.com/UsulPro/js-stack-from-scratch) by [React Theming](https://github.com/sm-react/react-theming)
- [ไทย](https://github.com/MicroBenz/js-stack-from-scratch) by [MicroBenz](https://github.com/MicroBenz)

만약 번역에 관심 있으시다면, [번역에 참가하는 방법](/how-to-translate.md)을 참고하여 바로 시작하세요!

## Credits

Created by [@verekia](https://twitter.com/verekia) – [verekia.com](http://verekia.com/).

License: MIT
