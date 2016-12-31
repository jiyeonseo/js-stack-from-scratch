# 3 - Babel과 Gulp를 이용한 ES6 설치

We're now going to use ES6 syntax, which is a great improvement over the "old" ES5 syntax. All browsers and JS environments understand ES5 well, but not ES6. So we're going to use a tool called Babel to transform ES6 files into ES5 files. To run Babel, we are going to use Gulp, a task runner. It is similar to the tasks located under `scripts` in `package.json`, but writing your task in a JS file is simpler and clearer than a JSON file, so we'll install Gulp, and the Babel plugin for Gulp too:

이제 ES6 구문을 사용해 봅시다. ES6 문법은 "오래된" ES5 문법을 크게 개선하였습니다. 모든 브라우저와 JS 환경은 ES5를 이해하지만 , 아직 ES6는 이해하지 못합니다. 따라서 Babel라는 ES6 파일을 ES5파일로 변환해주는 도구를 사용합니다. Babel을 실행하려면, 태스크 러너(task runner)인 Gulp을 사용합니다. 이전에 해보았던 `package.json`파일에 `scripts` 작성과 비슷하지만, 이번엔 작업들을 JSON 파일이 아닌 JS 파일에 작성하여 더 간단하고 깔끔하게 작성할 수 있습니다. 이를위해 Gulp과 Gulp용 Babel 플러그인도 설치합니다 :

- Run `yarn add --dev gulp`
- Run `yarn add --dev gulp-babel`
- Run `yarn add --dev babel-preset-latest`
- Run `yarn add --dev del` (for the `clean` task, as you will see below)
- In `package.json`, add a `babel` field for the Babel configuration. Make it use the latest Babel preset like this:

- `yarn add --dev gulp` 실행합니다
- `yarn add --dev gulp-babel` 실행합니다
- `yarn add --dev babel-preset-latest` 실행합니다
- `yarn add --dev del` 실행합니다 (이것은 아래 내용 중,`clean` 작업을 위한 것입니다)
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

- `build` is where Babel is called to transform all of our source files located under `src` and write the transformed ones to `lib`.
- `clean` is a task that simply deletes our entire auto-generated `lib` folder before every `build`. This is typically useful to get rid of old compiled files after renaming or deleting some in `src`, or to make sure the `lib` folder is in sync with the `src` folder if your build fails and you don't notice. We use the `del` package to delete files in a way that integrates well with Gulp's stream (this is the [recommended](https://github.com/gulpjs/gulp/blob/master/docs/recipes/delete-files-folder.md) way to delete files with Gulp).
- `main` is the equivalent of running `node .` in the previous chapter, except this time, we want to run it on `lib/index.js`. Since `index.js` is the default file Node looks for, we can simply write `node lib` (we use the `libDir` variable to keep things DRY). The `require('child_process').exec` and `exec` part in the task is a native Node function that executes a shell command. We forward `stdout` to `console.log()` and return a potential error using `gulp.task`'s callback function. Don't worry if this part is not super clear to you, remember that this task is basically just running `node lib`.
- `watch` runs the `main` task when filesystem changes happen in the specified files.
- `default` is a special task that will be run if you simply call `gulp` from the CLI. In our case we want it to run both `watch` and `main` (for the first execution).

**Note**: You might be wondering how come we're using some ES6 code in this Gulp file, since it doesn't get transpiled into ES5 by Babel. This is because we're using a version of Node that supports ES6 features out of the box (make sure you are running Node > 6.5.0 by running `node -v`).

Alright! Let's see if this works.

- In `package.json`, change your `start` script to: `"start": "gulp"`.
- Run `yarn start`. It should print "Hello ES6" and start watching for changes. Try writing bad code in `src/index.js` to see Gulp automatically showing you the error when you save.

- Add `/lib/` to your `.gitignore`

Next section: [4 - Using the ES6 syntax with a class](/tutorial/4-es6-syntax-class)

Back to the [previous section](/tutorial/2-packages) or the [table of contents](https://github.com/verekia/js-stack-from-scratch#table-of-contents).
