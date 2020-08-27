---
layout: post
title: JavaScript Object, this
subtitle: js, json
date: 2020-04-13T20:20:25.000Z
author: Arhrina
categories: update

tags: js
---

## JavaScript Object

자바스크립트의 객체는 properties와 values로 이루어진다

<h3>자바스크립트 객체(정확하게는 HTML 객체, 또는 HTML collection)는 js 명령어만을 들으며, jquery 명령어는 듣지 않는다. 반대도 마찬가지다</h3>

<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/innerImg/jsobject.png?raw=true">
class로 찾아와서 HTMLElement들의 collection이 조회되었다. id로 조회하게 되면 element만 조회된다. 이것에 접근하려면 .get(0) 등으로 java collection에 접근하듯이 접근해주어야한다



<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/innerImg/naverjqueryobject.png?raw=true">
jquery를 통해 DOM을 곧바로 처리하는 패턴이 지양되고 있고, 최근의 browser들은 DOM/BOM API를 잘 지원해주고 있으며, React, Angular, Vue같은 프론트엔드 라이브러리들에게 jquery가 주도권을 많이 넘겨주고 있기 때문에 최근 추세는 탈jquery이다


<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/innerImg/jqueryObject.png?raw=true">
debugger를 걸어두고 jquery로 jquery 객체를 선택해보았다. .get(0) 등으로 html element에 접근하게 되면 jquery 함수는 통하지 않고, js 함수가 통하게 된다






js와 jquery의 사용시에 console창에서 오류가 발생하는 부분에 대한 것은, 실행순서에 대해 별도로 포스팅을 하겠다



<img src="https://github.com/arhrina/arhrina.github.io/blob/master/assets/img/innerImg/naverjqueryobject.png?raw=true">


변수는

```javascript
var car = ferrari;
```

방식으로 선언되어서 자료에 따라 변수의 자료형이 정해진다

변수는 하나에 하나의 값만을 담을 수 있지만, object는 여러개의 값을 담을 수 있다

```java
Map<String, String> car = new HashMap<String, String>();
car.put("name", "ferrari");
car.put("color", "red");
car.put("horsePower", "670"); //  String에 String으로 선언하였으므로 본래 들어가야할 숫자가 아닌 문자열로 값을 넣었다
```



자바에서의 Key, Value 쌍으로 저장되는 Map과 같이 자바스크립트의 object도 name, value 쌍으로 저장된다



```javascript
var car = { name:"ferrari", color:"red", horsePower:670};
```

읽기 편하게 중간에 공백이나 줄바꿈을 하여도 같은 결과를 얻는다

```javasciprt
var car = {
	name : "ferrari",
	color : "red",
	horsePower : 670
};
```

이러한 object에 대한 접근은,

<b>objectName.propertyName</>이나

<b>objectName["propertyName"]</b>으로 접근한다

```javascript
console.log(car.name);
console.log(car["name"]);
```

메서드를 value로 지정해서 저장할 수도 있으며 이럴 경우 메서드를 사용할 이름은 property가 된다

```javasciprt
var car = {
	speed : 0;
	accelerator : function(){ return this.speed = 350; }
	};

car.accelerator(); // 메서드임을 의미하는 괄호는 반드시 작성되어야한다. 안해주면, 메서드의 정의를 return한다
console.log(car.speed); // 출력값은 350
```

### String, Number, Boolean으로 객체를 선언하는 것은 피하자. 코드의 성능에 지장을 미친다




## JavaScript의 중요한 키워드, this

자바스크립트에서 this는 this가 속해있는 scope를 참조하고 있는 범위를 뜻한다

<h4>어디서 쓰이고 있는지가 가장 중요하다</h4>

예를 들어서, 메서드 안에서 쓰이는 this는, this를 가지고 있는 객체(메서드가 정의된)를 뜻한다

```javascript
var language = {
	myFirst : "C",
	mySecond : "Cpp",
	myThird : "Java",
	myFirstLanguage : function() {
		return this.myFirst + " is my First learning language"; // 이 경우 this가 속해있는 메서드를 가지고 있는 object는 language이다.
	}
};
```

this가 혼자 쓰인다면 global object를 뜻하며, strict mode("use strict";를 사용한 모드. 추후 포스팅)에서는 this는 undefined(java로 굳이 치자면 null point exception이 뜰 값. null이나 문자열 ""과는 엄연히 다르다)

html(혹은 js) 이벤트 안에서는 element를 뜻한다


```javascript
<button onclick="this.style.background-color='green'">
  클릭하면 녹색됨 // this는 여기서 element인 button
</button>
```


<h4>이러한 this의 사용 scope를 항상 주의해서 사용해야하며, 잘 사용하면 아주 편리하게 코드를 짤 수 있다</h4>