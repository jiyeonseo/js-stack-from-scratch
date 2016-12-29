# 1 -  Node와 NPM, Yarn, 그리고 package.json

이 장에서는 Node, NPM, Yarn, 그리고 기본적인 `package.json`파일의 설정 방법을 알아봅니다.

먼저 JavaScript 백엔드 뿐만 아니라, 모던 프론트엔드 스택을 구축하기위한 도구로 Node를 설치해야합니다.

macOS 및 Windows의 경우, 바이너리 [다운로드 사이트](https://nodejs.org/en/download/current/)를 이용하거나,  Linux 배포판용 패키지 매니저 [설치 페이지](https://nodejs.org/en/download/package-manager/)를 이용합니다.

For instance, on **Ubuntu / Debian**, you would run the following commands to install Node:

예를 들어, **Ubuntu 또는 Debian** 이면 다음 명령을 이용해 Node 설치합니다.

```bash
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Node의 버전은 6.5.0 이상이면 어떤 버전이든 상관 없습니다.

Node의 기본 패키지 매니저인 `npm`은 Node 안에 포함되어 있기 때문에 별도로 설치할 필요가 없습니다.

**주의** : Node가 이미 설치되어있는 경우, nvm([Node Version Manager](https://github.com/creationix/nvm))을 설치하고 `nvm`을 이용하여 최신 Node를 설치하십시오.

[Yarn](https://yarnpkg.com/) 은 NPM보다 빠른 또 다른 패키지 매니저로, 오프라인 환경도 지원하며, 디펜던시를 [더 예상대로 ](https://yarnpkg.com/en/docs/yarn-lock) 가져옵니다. Yarn은 2016 년 10월에 [출시](https://code.facebook.com/posts/1840075619545360)된 이후, 새로운 패키지 매니저의 대안으로 JavaScript 커뮤니티에서 급속도로 적용되고 있습니다. 이 튜토리얼에서는 Yarn을 사용합니다. NPM을 사용하려면, `yarn add`과 `yarn add --dev` 을 `npm install --save`과 `npm install --save-dev` 와 같이 대체하시면 됩니다.

- [설치 방법](https://yarnpkg.com/en/docs/install)에 따라 Yarn을 설치합니다. `npm install -g yarn` 혹은 `sudo npm install -g yarn` 으로 설치 할 수 있습니다. (오! NPM을 이용하여 Yarn을 설치해보았습니다. 마치, Internet Explorer나 Safari를 사용하여 Chrome을 설치한 것 같군요!)

- 새로운 작업 폴더를 만들고 `cd`를 이용해 이동합니다.

- `yarn init`을 실행하고 몇몇 질문에 답하면 (`yarn init -y`으로 모든 질문을 건너 뛸 수 있습니다) `package.json`파일이 자동 생성됩니다.

- `index.js`파일을 만들고 `console.log('Hello world')`를 작성합니다.

- 현재 폴더에서 `node .`를 실행합니다. (`index.js`는 현재 폴더 내에서 Node가 검색하는 기본 파일 이름입니다). "Hello world"로 표시되는 모습을 보실 수 있습니다.

`node .`으로 프로그램을 실행시키는 것은 다소 low-level의 방법입니다. 대신 NPM/Yarn 스크립트를 사용하여 코드를 실행해 봅시다. 멋지게 추상화를 해 놓으면, 후에 더 복잡한 프로그램의 경우에도 `yarn start`만으로도 실행 할 수 있습니다.

- `package.json`안에, `scripts` 라는 객체와 함께 다음과 같이 작성합니다.

```json
"scripts": {
  "start": "node ."
}
```

`package.json` 반드시 올바른 JSON 파일이여야 하기 때문에 마지막에 쉼표가 붙지 않도록 해야합니다. `package.json` 파일을 수동으로 편집할때 꼭 주의하십시오.

- `yarn start`로 실행하면 `Hello world`가 출력되는 것을 보실 수 있습니다.

- `.gitignore`파일을 만들고 다음과 같이 내용을 추가합니다.

```gitignore
npm-debug.log
yarn-error.log
```

**주의** : 각 챕터 내 `package.json`파일에 `tutorial-test`라는 스크립트가 있습니다. 이 스크립트는 자기 자신을 테스트 하는 스크립트로, `yarn && yarn start`로 실행시켜 볼 수 있습니다. 다른 프로젝트에서 사용하는 경우, 삭제해도 상관 없습니다.

다음 장 : [2 - 패키지의 설치 및 사용](/tutorial/2-packages)

[목차 로 돌아 가기](https://github.com/verekia/js-stack-from-scratch#table-of-contents).
