# 2 - 패키지 설치와 사용

이 챕터에서는 패키지를 설치하고 사용하는 방법에 대해서 알아봅니다. "패키지"는 다른 사람이 작성한 코드의 조각으로, 여러분의 코드 내에서 사용할 수 있습니다. 예제로 색상을 처리하는 것을 도와줄 패키지를 사용해 보도록 하겠습니다.

- 커뮤니티에서 만들어진 패키지 `color`를 설치하기 위해 `yarn add color`를 실행합니다.

`package.json`을 열면, Yarn이 `dependencies`안에 `color`를 자동으로 추가 한 것을 볼 수 있습니다.

패키지를 저장하기 위해 `node_modules`폴더가 만들어 진 것을 확인 할 수 있습니다.

- `.gitignore`파일에 `node_modules/`를 추가합니다. (아직 `git init`을 하지 않았다면, 지금 `git init`을 실행합니다)

`yarn.lock`이라는 파일이 Yarn에 의해 생성 된 것을 보실 수 있습니다. 이 파일은 반드시 저장소에 커밋되어야 하는데, 이렇게 해두어야 팀의 모든 구성원이 동일한 버전의 패키지를 이용할 수 있게 됩니다. 만약 Yarn 대신 NPM을 사용한다면, *shrinkwrap*로 대체할 수 있습니다.

- `index.js`파일에 `const Color = require('color');`와 같이 작성합니다.
- 예를 들어, 다음과 같은 형태로 패키지 사용해 볼 수 있습니다 : `const redHexa = Color({r: 255, g: 0, b: 0}).hex();`
- `console.log(redHexa)`를 추가합니다.
- `yarn start`로 실행하면 `#FF0000`나타나는 것을 볼 수 있습니다.

축하드립니다! 패키지 설치와 사용을 모두 해보았습니다!

`color` is just used in this section to teach you how to use a simple package. We won't need it anymore, so you can uninstall it:
`color`는 이 챕터에서 패키지의 사용법을 설명하기 위한 그냥 단순한 패키지입니다. 이제 필요없는 때문에 삭제해보도록 하겠습니다:

- `yarn remove color`를 실행합니다.

**주의** : 패키지 디펜던시에는 `"dependencies"`과 `"devDependencies"`의 2 종류가 있습니다. `"dependencies"`는 `"devDependencies"`보다 일반적인 것으로, 후자는 개발하는 동안에만 사용되는 패키지이며, 제품 환경에서는 사용하지 않습니다. (일반적으로 빌드와 관련된 패키지, linter 등이 있습니다). `"devDependencies"`에 추가하려면 `yarn add --dev [package]`  와 같이 실행합니다.

다음 챕터 : [3 - Babel과 Gulp를 이용한 ES6 설치](/tutorial/3-es6-babel-gulp)

[전 챕터](/tutorial/1-node-npm-yarn-package-json) 또는 [목차](https://github.com/verekia/js-stack-from-scratch#table-of-contents)로 돌아 가기
