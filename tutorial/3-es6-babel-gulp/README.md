# 3 - Babel과 Gulp를 이용한 ES6 설치

이제 ES6 문법을 사용해 봅시다. ES6 문법은 "오래된" ES5 문법을 크게 개선하였습니다. 모든 브라우저와 JS 환경은 ES5를 이해하지만, 아직 ES6는 이해하지 못합니다. 따라서 Babel라는 ES6 파일을 ES5 파일로 변환해주는 도구를 사용합니다. Babel을 실행하려면, 태스크 러너(task runner)인 Gulp을 사용합니다. 이전에 해보았던 `package.json`파일에 `scripts` 작성과 비슷하지만, 이번엔 작업들을 JSON 파일이 아닌 JS 파일에 작성하여 더 간단하고 깔끔하게 작성할 수 있습니다. 이를 위해 Gulp과 Gulp용 Babel 플러그인도 설치합니다 :

- `yarn add --dev gulp` 실행합니다.
- `yarn add --dev gulp-babel` 실행합니다.
- `yarn add --dev babel-preset-latest` 실행합니다.
- `yarn add --dev del` 실행합니다. (이것은 아래 내용 중,`clean` 작업을 위한 것입니다)
- `package.json`파일에 Babel 설정을 위한 `babel`필드를 추가합니다. 최신 Babel 설정을 사용하려면 다음과 같이합니다 :

```json
"babel": {
  "presets": [
    "latest"
  ]
},
```

**주의** : `.babelrc`파일이 프로젝트의 루트에 있는 경우 `package.json`내의 `babel`보다 우선됩니다. 시간이 지날수록 루트 폴더가 점점 더 거대해 질 것이기 때문에, Babel 설정이 너무 커지기 전까지 `package.json`에 작성해 보겠습니다.

- `index.js`파일을 새로운 `src`폴더로 이동 시킵니다. ES6의 코드를 작성하기 위한 폴더입니다. `lib`폴더는 컴파일 된 ES5 코드가 들어갈 폴더입니다. Gulp와 Babel을 이용해 코드 생성을 할 것입니다. `index.js`파일에서 전 챕터의 `color` 관련 코드를 삭제하고 다음과 같이 간단한 코드를 작성해봅니다:

```javascript
const str = 'ES6';
console.log(`Hello ${str}`);
```

여기에서 *템플릿 문자열(template string)*을 사용하고 있습니다. 이것은 ES6의 새로운 문법에서 ${}를 사용한 문자열은 별도의  연결없이 변수를 직접 문자열에 삽입하는 것입니다. 템플릿 문자열 에서는 ***역 따옴표**를 사용하고있는 점에 유의하십시오.

- 다음과 같이 `gulpfile.js`를 만듭니다:

```javascript
const gulp = require('gulp');
const babel = require('gulp-babel');
const del = require('del');
const exec = require('child_process').exec;

const paths = {
  allSrcJs: 'src/**/*.js',
  libDir: 'lib',
};

gulp.task('clean', () => {
  return del(paths.libDir);
});

gulp.task('build', ['clean'], () => {
  return gulp.src(paths.allSrcJs)
    .pipe(babel())
    .pipe(gulp.dest(paths.libDir));
});

gulp.task('main', ['build'], (callback) => {
  exec(`node ${paths.libDir}`, (error, stdout) => {
    console.log(stdout);
    return callback(error);
  });
});

gulp.task('watch', () => {
  gulp.watch(paths.allSrcJs, ['main']);
});

gulp.task('default', ['watch', 'main']);

```

이제 하나씩 천천히 알아가 봅시다.

Gulp의 API는 매우 직관적입니다. `gulp.task`를 정의하고, 그 속에서 `gulp.src`에서 파일을 참조하고, `.pipe()`를 사용하여 (마치 `babel()`처럼) 일련의 작업을 체인으로 묶어주고, 최종적으로 `gulp.dest`라는 새로운 파일로 출력합니다.
또한, `gulp.watch`를 이용해 파일시스템의 변화 역시 감지할 수 있습니다. Gulp 작업을 시작하기 전에 필요한 작업을 먼저 실행 할 수 있습니다. `gulp.task`의 두번째 인자에 배열의 형태로 (예를 들어, `['build']`)전달해 먼저 작업을 수행 시킬수 있습니다. 보다 자세한 소개는 [문서](https://github.com/gulpjs/gulp)를 참조하시기 바랍니다.

먼저, 다른 파일 경로를 바라볼 수 있도록  `paths` 객체를 정의합니다.

이어서 5개의 작업을 정의 합니다. : `build`, `clean`, `main`, `watch`, `default`


- `build`는 `src` 아래의 소스 파일을 변환하여 `lib`로 옮기는 작업입니다.

- `clean` build를 하기 전에 `lib` 폴더 안에 자동 생성되는 모든 파일들을 삭제하는 작업입니다. 이 작업은 `src` 내부의 파일 이름이 변경되거나 삭제된 후 예전에 컴파일된 파일들을 지우거나, 혹시나 모르는 필드 실패를 대비한 `lib`폴더와 `src` 폴더 동기화를 확실히 해주기 위해 사용 됩니다. 이 작업은 `src` 내부의 파일 이름을 변경 또는 삭제하거나 빌드에 실패한 사실을 모르는 경우 lib폴더를 src폴더에 확실하게 동기화시키기 위해 생성 된 파일을 삭제하는 데 유용합니다.Gulp 스트림과 연계하여 파일을 삭제하기 위해 여기에서는 `del`패키지를 사용하고 있습니다. (이 방법은 Gulp에서 파일 삭제 방법으로 [권장](https://github.com/gulpjs/gulp/blob/master/docs/recipes/delete-files-folder.md)하는 방법입니다)

- `main` 는 앞 챕터에서 `node .` 실행시키고있는 해당하며, `lib/index.js` 에서 실행되는 점이 다릅니다. `index.js`는 Node가 기본으로 찾는 파일 이름이므로, 간단히 `node lib`라고 작성할 수 있습니다. (코드 중복을 막기 위해 이 튜토리얼에서는 `libDir`변수를 사용합니다.) `require('child_process').exec`와 `exec` 작업은 쉘 명령을 실행하는 Node의 표준 함수입니다. `stdout`을 `console.log()`로 넘겨 로그를 찍고, `gulp.task`의 콜백 함수를 사용하여 잠재적 에러를 반환합니다. 이 부분이 명확하게 이해하지 못해도 걱정할 필요는 없습니다. 이 작업은 기본적으로 `node lib` 실행하기위한 것이라고만 기억하면 됩니다.

- `watch`는 특정 파일에 업데이트가 있는 경우 `main` 작업을 실행합니다.

- `default`는 CLI를 통해 `gulp`를 실행한 경우 호출되는 특수 작업입니다. 이 튜토리얼에서는 `watch`와 `main`이 동시에 실행되도록 하겠습니다. (첫번째 실행에서)

**주의** : 이 Gulp 파일이 Babel에 의해 ES5로 변환되지 않은 ES6로 작성되어있는데 괜찮은지 궁금하실 지도 모릅니다. 이 튜토리얼에서는 ES6를 표준으로 지원하는 버전의 Node를 사용하고 있기 때문에 문제없습니다.(`node -v`를 실행하여 버전 6.5.0 이상의 Node를 사용하고 있는지 확인하십시오)


자! 이제 잘 작동하는지 살펴봅시다.

- `package.json` 내부의 `start` 스크립트를 `"start": "gulp"`로 변경합니다.
- `yarn start`로 실행하면 "Hello ES6"라고 나오며 변경 모니터링이 시작됩니다. `src/index.js` 잘못된 코드를 작성 해보고, 저장할 때 Gulp가 자동으로 오류를 표시하는지 시험해 봅시다.
- `/lib/`를 `.gitignore`파일 에 추가합니다.


다음 챕터: [4 - class를 이용한 ES6 문법 사용](/tutorial/4-es6-syntax-class)
[전 챕터](/tutorial/2-packages) 또는 [목차](https://github.com/jiyeonseo/js-stack-from-scratch#table-of-contents)로 돌아 가기
