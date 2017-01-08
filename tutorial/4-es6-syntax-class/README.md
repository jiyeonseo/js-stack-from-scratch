# 4 - class를 이용한 ES6 문법 사용

- 새 파일 `src/dog.js`를 만들고 다음과 같이 ES6 클래스를 작성합니다. :

```javascript
class Dog {
  constructor(name) {
    this.name = name;
  }

  bark() {
    return `Wah wah, I am ${this.name}`;
  }
}

module.exports = Dog;
```

이전에 다른 언어로 OOP를 해본 적이 있다면, 그닥 놀라운 점은 없을 것입니다. 그러나 JavaScript에 클래스 구문이 도입 된 것은 꽤나 최근일 입니다. 이 클래스는 `module.exports`에 대입됨으로써 외부 세계에 노출됩니다.

ES6 코드는 클래스를 사용하며, `const`와 `let`을 사용하고, bark()과 같이 "템플릿 문자열(template strings)", 그리고 이 예제에서는 사용되지 않았지만 화살표 함수(arrow function) (`(param) => { console.log('Hi'); }`)를 사용합니다.

`src/index.js`파일에 다음과 같이 작성합니다. :

```javascript
const Dog = require('./dog');

const toby = new Dog('Toby');

console.log(toby.bark());
```

전에 사용했던 `color`패키지와는 달리, 자신이 만든 파일을 require 할 때는 `require()`내부에서 `./`를 이용합니다.

- `yarn start`를 실행합니다. 'Wah wah, I am Toby'로 나타나는 것을 보실 수 있습니다.

- `lib`안에 생성 된 코드를 보고 컴파일 된 코드는 어떻게 되어있는지 확인해 봅니다. (예를 들어, `const`대신 `var` 등)

다음 챕터: [5 - ES6 모듈 문법](/tutorial/5-es6-modules-syntax)

[전 챕터](/tutorial/3-es6-babel-gulp) 또는 [목차](https://github.com/jiyeonseo/js-stack-from-scratch#table-of-contents)로 돌아 가기
