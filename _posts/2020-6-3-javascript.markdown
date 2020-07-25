---
layout: post
title: js의 실제사용
subtitle: js
date: 2020-06-03T15:14:25.000Z
author: Arhrina
categories: update
cover: '../assets/img/cover/'
tags: js, jquery
---

## js를 실제 사용하면서 느낀 것들

css와 사용이 매우 유사하다. selector를 통해 원하는 것을 지정하고, 그에 따른 동작을 지정한다

원하는 것을 지정할 때, html 문서 전체를(혹은 jsp 전체를) 객체로 만들어주는 document를 사용하여 시작한다

```javascript
document.getElementById("지정할 id"); // 하나의 Element만을 지정한다. Id로 지정할 것을 이미 선언하였으므로 #은 붙이지 않는다
document.getElementsByClasses("지정할 클래스"); // 함수명에도 나와있다시피 Elements를 지정한다. 클래스를 지정할 것을 선언하였으므로 .은 붙이지 않는다
```

이렇게 지정한 것을 변수 등에 담아서 사용하면 편리하다

```javascript
let tbody = document.getElementById("tbody의 id");

let tr = document.createElement("tr"); // <tr></tr>이 tr에 생성된다

tr.innerHTML = "<td>예제한줄</td>";

tbody.appendChild("tr");
```

tr을 하나 만들어서 안에 td를 붙여주고 이를 tbody의 가장 마지막에 붙여주는 예제코드이다

html DOM을 따로 별개의 문서를 만들어서 넣어주는 방법도 존재한다

checked:check를 통해 체크박스에서 체크된 것을 확인하여 closest 등의 함수를 사용해 해당하는 한 줄을 지정하여 원하는 값을 서버로 보내줄 수 있게 코딩을 할 수 있게 된다

js 코드는 jquery로 짜는 코드보다 기므로 jquery로 짜면 좀 더 가독성이 좋게 만들 수도 있다(특정 상황에서는 js가 더 가독성이 좋을 수도 있다)


```javascript
// 위 예제 코드를 jquery로 만들어보자면
let tbody = $("#tbody의 id"); // jquery로 사용할 수 있도록 $를 붙이고 id 셀렉터를 사용하므로 #을 사용

// 아래 코드를 한줄로 체이닝하여 만들 수도 있다
// 코드 버전별, 브라우저별로 성능을 볼 수 있는 <a href="https://stackoverflow.com/questions/268490/jquery-document-createelement-equivalent">overflow 페이지</a>
let tr = $(document.createElement("tr"));
tr.HTML("<td>예제한줄</td>");
tbody.append(tr);
```

정확한 셀렉터를 사용하여 범위를 좁혀 사용하는 것이 js와 jquery의 사용에 있어서 중요한 사안이다. 그렇게하면 팝업을 열어 부모창과 자식창이 통신을 하는 응용에서도 문제 없이 코드를 짤 수 있게 된다

js의 this 키워드에 대해서는 스코프를 잘 이해하고 사용하게 된다면 짧은 코드를 만들게 될 수 있고, 코드의 변경에 있어서 좀 더 유연한 코드를 짤 수 있게 되므로 필히 공부하자