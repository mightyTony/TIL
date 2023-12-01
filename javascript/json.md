## JSON (JavaScript Object Notation)


- 데이터 전달을 위한 표준 포맷
- 문자, 숫자, 불린, Null, 객체, 배열만 사용
- 문자는 큰 따옴표만 사용
- 후행 쉼표 사용 불가
- .json 확장자 사용

```
JSON.stringify() - 데이터를 JSON 문자로 변환 합니다.
JSON.parse() - JSON 문자를 분석해 데이터로 변환 합니다.
```

```javascript
console.log(JSON.stringify('Hello world')) => "Hello world"
console.log(JSON.stringify(123)) => 123

console.log(JSON.parse('"Hello world"')) => Hello world!

```
