# 5 - ES6 모듈 문법

`const Dog = require('./dog')`를 `import Dog from './dog'`로 바꿔봅니다. 이것이 ("CommonJS" 모듈 문법에 비해) 새로운 ES6 모듈의 문법입니다.

`dog.js` 내부의 `module.exports = Dog`을 `export default Dog`으로 바꿉니다.

`dog.js`내에서 `Dog`이라는 이름은 `export`안에서만 사용되는 점을 유의하십시오. 따라서 다음과 같이 익명 클래스로 직접 내보낼 수 있습니다 :

```javascript
export default class {
  constructor(name) {
    this.name = name;
  }

  bark() {
    return `Wah wah, I am ${this.name}`;
  }
}
```

눈치 채셨을지 모르겠지만, `index.js`파일의 `import`에서 'Dog'이라는 이름은, 사용하는 사람 마음대로 입니다. 실제로 이렇게 써도 문제없이 동작합니다.

```javascript
import Cat from './dog';

const toby = new Cat('Toby');
```

물론, 가져온 class / module의 이름을 그대로 사용하는 경우가 대부분입니다.
그렇지 않은 예로는, Gulp 파일에서 `const babel = require('gulp-babel')`하는 경우가 있습니다.

그렇다면, `gulpfile.js`파일의 `require()`는 어떨까요? 대신 `import`를 사용할 수 있을까요? 최신 버전의 Node는 ES6의 대부분의 기능을 지원하고 있지만, ES6 모듈 기능은 아직 지원하지 않습니다. 하지만 다행히 Gulp는 Babel의 도움을 받을 수 있습니다. `gulpfile.js`를 `gulpfile.babel.js`로 이름을 바꾸면 Babel은 `import`된 모듈을 Gulp에 전달하는 역할을 해줍니다.

- `gulpfile.js`를 `gulpfile.babel.js`로 이름을 바꿉니다.

- `require()`를 다음과 같이 수정합니다.

```javascript
import gulp from 'gulp';
import babel from 'gulp-babel';
import del from 'del';
import { exec } from 'child_process';
```

`child_process`에서 `exec`를 직접 접근하기 위해 문법적 설탕(syntactic sugar)이 사용되었습니다. 정말 멋지지 않습니까!

- `yarn start`를 실행하면 "Wah wah, I am Toby"로 나타나는 것을 보실 수 있습니다.


다음 챕터: [6 - ESLint](/tutorial/6-eslint)

[전 챕터](/tutorial/4-es6-syntax-class) 또는 [목차](https://github.com/jiyeonseo/js-stack-from-scratch#table-of-contents)로 돌아 가기
