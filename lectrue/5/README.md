# 강의 5

## 1. 웹팩 데브 서버

* 실습 진행

## 2. ES6

### 변수

* ES6 부터는 **일반적인 프로그래밍언어와 비슷한 Scope**를 가진 선언문 2가지를 지원한다.
  * 기존 선언문인 ```var```는 ```{}```에 관계없이 사용 가능하여 변수 scope 에 대해 오해나 문제가 생길수 밖에 없다.

* ```let```
  * 재할당 가능
* ```const```
  * 재할당 불가능 
  * Java의 ```final```과 같다.

### 함수

* ES6에서는 Java의 람다식과 같은 arrow function을 지원한다.

```js
var sum = function (a, b) {
    return a + b;
};

console.log(sum(10, 20));
```

위 코드에서 ```function (a, b)``` 는 아래와 같이 변경 가능하다.

```js
var sum = (a, b) => {
    return a + b;
};

console.log(sum(10, 20));
```

**절대하면 안되는것**

```js
실행컨텍스트 연장

var vm = this;
axios.get(url)
    .then(function (response) {
        console.log(response);
        vm.user = response.data;
    })
    .catch(function (error) {
        console.log(error);
    });
```

```js
fetchUser: function () { // 이걸 ()=> 로 변환하면 안된다.
    console.log(this);
    var url = 'https://jsonplaceholder.typicode.com/users/1';
    var vm = this;
    axios.get(url)
        .then(function (response) {
            console.log(response);
            vm.user = response.data;
        })
        .catch(function (error) {
            console.log(error);
        });
}
```

### 객체 선언

* JS에서는 객체 선언시 **축약 문법**을 지원한다.

```js
var num = 10;
var obj = {
    num:num // 위에서 선언한 num
};

console.log(obj.num);
```

위 코드는 JS에서 아래 코드와 동일한 결과를 나타낸다.

```js
var num = 10;
var obj = {
    num // 위에서 선언한 num과 이름이 같으니 생략이 가능하다.
};

console.log(obj.num);
```

* 즉, 객체를 정의할 때 **속성(property)와 미리 선언된 값(value)이 같으면** 축약이 가능하다.

좀 더 확장하면 다음도 가능하다.

```js
var router = {
  routes: [
    {
      path: 'sth',
      component: 'sthComponent',
    },
  ],
};

function example() {
  return {
    router: {
      routes: [
        {
          path: 'sth',
          component: 'sthComponent',
        },
      ],
    }
  };
}
```

위 코드와 아래 코드는 일치한다.

```js
var router = {
  routes: [
    {
      path: 'sth',
      component: 'sthComponent',
    },
  ],
};

function example() {
  return {
    router // router 이름이 같아서 생략
  };
}


```

### 모듈화

Tip)

```js
import {} from ''; 
```

* 위와 같이 선언하면 **자동 완성**이 쉽게 된다.


```js
export default function sum(a, b) {
    return a + b;
}

import sum from './util';
```

## 3. jQuery -> Vuejs로 변환하기

## Q & A

### JS 진영의 표준 파일/디렉토리 컨벤션은?

* [사이트](https://joshua1988.github.io/vue-camp/advanced/folder-structure.html#%EB%B7%B0-cli%EB%A1%9C-%EC%83%9D%EC%84%B1%ED%95%9C-%EA%B8%B0%EB%B3%B8-%ED%8F%B4%EB%8D%94-%EA%B5%AC%EC%A1%B0) 참고 하면 좋음