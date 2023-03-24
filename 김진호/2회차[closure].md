# Closure
클로저는 자바스크립트 고유의 개념이 아니라 함수를 **일급 객체**로 취급하는 함수형 프로그래밍 언어에서 사용되는 중요한 특성.     
> 클로저는 함수와 그 함수가 선언됐을 때의 렉시컬 환경(Lexical environment)과의 조합이다.

```js
function outerFunc(){
    var x = 10;
    var innerFunc = function(){console.log(x);};
    innerFunc();
}

outerFunc();

```
```innerFunc``` 가 함수 ```outerFunc```의 내부에 선언되어 있기 때문에 ```outerFunc```의 변수 x에 접근할 수 있다.

