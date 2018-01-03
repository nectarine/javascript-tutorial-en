# 자바스크립트에 대한 소개

자바스크립트가 어째서 그렇게 특별한지, 그것으로 무엇을 할 수 있는지, 그리고 같이 사용하는 다른 기술들은 뭐가 있는지 살펴보겠습니다.

## 자바스크립트란 무엇인가?

*자바스크립트*는 최초에 *"웹페이지를 살아움직이게 하도록"* 만들어졌습니다.

이 언어로 만들어진 프로그램은 *스크립트*라고 불립니다. HTML속에 바로 작성될 수 있으며 페이지가 로드될 때 자동으로 실행됩니다.

스크립트는 평문으로 제공되고 실행됩니다. 실행하기 위한 특별한 준비나 컴파일이 필요하지 않습니다.

이러한 측면에서, 자바스크립트는 [자바](http://en.wikipedia.org/wiki/Java) 언어와 굉장히 다릅니다.

```smart header="왜 <u>자바</u>스크립트인가?"
자바스크립트가 만들어졌을 때, 처음에는 "LiveScript"라는 이름을 가지고 있었습니다. 그러나, 자바 언어가 그 당시에 굉장히 인기가 있었고, 자바의 "어린 형제"처럼 포지셔닝해서 그 인기에 편승하기 위해 이름이 결정되었습니다.

그러나 언어가 진화되면서 자바스크립트는 완전히 독립적인 언어가 되었고, [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript)라는 독립적인 표준을 가집니다. 이제는 자바와는 아무런 관계가 없습니다.
```

현재 시점에서는 자바스크립트는 브라우저뿐만 아니라 서버나 [자바스크립트 엔진](https://en.wikipedia.org/wiki/JavaScript_engine)을 탑재한 어느 곳에서나 실행될 수 있습니다.

브라우저는 내장 엔진을 지니고 있고, 때때로 "자바스크립트 가상 머신"이라고 불리웁니다.

각각의 엔진은 다른 "코드네임"을 지니고 있는데, 예를 들어:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- 크롬과 오페라.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- 파이어폭스.
- ...IE의 다양한 버전들에서 사용되는 "Trident", "Chakra", 마이크로소프트 엣지에서 사용되는 "ChakraCore", 사파리나 기타 브라우저에서 사용되는 "Nitro" and "SquirrelFish" 등이 있습니다.

위의 용어들은 기억해두면 좋습니다. 개발 관련 글들에서 사용되며, 우리도 그 용어를 사용할 것입니다. 예를 들어, "기능 X는 V8에서 지원된다"라는 의미는 크롬과 오페라에서 동작한다는 뜻입니다.

```smart header="엔진은 어떻게 동작할까?"

엔진은 복잡합니다. 하지만 기본은 간단합니다.

1. 엔진이 (브라우저라면 내장되어있는) 스크립트를 읽습니다.("분석합니다.").
2. 스크립트를 기계어로 변환("컴파일")합니다.
3. 기계어가 실행되고, 꽤 빠릅니다.

엔진은 모든 단계에서 최적화를 적용합니다. 심지어 컴파일된 스크립트가 실행될때 감시하고 있다가, 주어지는 데이터를 분석하고 그 데이터를 기반으로 해서 최적화를 수행합니다. 결국에는 스크립트는 굉장히 빠르게 실행됩니다.
```

## 브라우저 내의 자바스크립트는 무엇을 할 수 있을까?

현대적인 자바스크립트는 "안전한" 프로그래밍 언어입니다. 저차원의 메모리나 CPU 접근을 제공하지 않으며, 이는 자바스크립트가 최초에 브라우저를 위해서 만들어졌으며 브라우저에서는 그것들이 필요하지 않기 때문입니다.

자바스크립트의 역량은 실행되는 환경에 크게 의존합니다. 예를 들어, [Node.JS](https://wikipedia.org/wiki/Node.js)는 임의의 파일을 읽고 쓰거나, 네트워크 요청을 수행할 수 있는 기능을 지원합니다.

브라우저 내의 자바스크립트는 웹페이지 조작, 사용자와 웹서버의 상호작용에 관련된 모든 것을 할 수 있습니다.

예를 들어, 브라우저 내의 자바스크립트는 아래의 것들이 가능합니다:

- 새로운 HTML을 페이지에 추가하기, 존재하는 내용을 변경하기, 스타일을 변경하기.
- 사용자의 동작에 반응하기, 마우스 클릭, 마우스 포인터의 움직임, 키보드 입력 시에 스크립트 실행하기.
- 네트워크를 통해 원격 서버로 요청 전송하기, 파일을 다운로드하거나 업로드하기 ([AJAX](https://en.wikipedia.org/wiki/Ajax_(programming))와 [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) 기술로 불립니다).
- 쿠키를 가져오거나 설정하기, 방문자에게 질문하기, 메시지를 표시하기.
- 클라이언트 사이드에 데이터를 기억하기 ("로컬 저장소").

## 브라우저 내의 자바스크립트는 무엇을 할 수 없을까?

브라우저 내의 자바스크립트의 능력은 사용자의 안전을 위해 제약됩니다. 나쁜 웹페이지가 개인 정보에 접근하거나, 사용자의 데이터에 해를 입히기 못하게 하기위한 목적입니다.

이러한 제약의 예로는:

- 웹페이지상의 자바스크립트는 하드디스크 상의 임의의 파일을 읽고 쓰거나, 복사하거나, 실행할 수 없습니다. 또한 OS 시스템 함수에 직접 접근할 수 없습니다.

    현대의 브라우저들은 파일에 대한 작업을 허용하지만, 사용자가 해당 파일을 브라우저 창에 "드롭핑"하는 것 같은 특정 동작을 했을때나 `<input>` 태그를 통해서 선택된 파일에 대해서만 허용하고 나머지는 제약되어있습니다.

    카메라, 마이크 혹은 다른 기기들과 상호작용할 수 있는 방법이 있지만 사용자의 명시적인 허가가 필요합니다. 그래서 자바스크립트가 활성화된 페이지는 몰래 웹카메라를 켜서 주변을 관찰한다음 그 정보를 [NSA](https://en.wikipedia.org/wiki/National_Security_Agency)로 보내지 못합니다.
- 서로 다른 탭/창들은 일반적으로 서로를 알지 못합니다. 때때로 알게 될 때도 있는데, 자바스크립트를 사용하는 창이 새로운 창을 열려고 할 때 그렇습니다. 그러나 이러한 경우에도 다른 사이트를 호출하는 경우(도메인, 프로토콜, 포트 등이 다르면) 해당 페이지의 자바스크립트는 다른 페이지에 접근할 수 없습니다.

    이것을 "동일 출처 정책"이라고 합니다. 이것을 피하기 위해서는 *양쪽의 페이지 모두* 데이터 교환을 처리하는 특수한 자바스크립트 코드를 포함해야합니다.

    이 제약은 역은 사용자의 안전을 위해서입니다. 사용자가 `http://anysite.com`를 통하여 연 페이지는 `http://gmail.com` URL로 열린 다른 탭에 접근할 수 없어야하며, 그곳으로부터 정보를 훔칠 수 없어야합니다.
- 자바스크립트는 현재 페이지가 전달된 서버와 네트워크를 통하여 쉽게 통신할 수 있습니다. 그러나 다른 사이트/도메인으로부터 데이터를 전달받는 것은 문제가 발생합니다. 설사 가능하더라도, 명시적인 합의 (HTTP 헤더에 표현된)가 원격부에서 필요합니다. 다시 한번, 이것은 안전 제약입니다.

![](limitations.png)

이러한 제약은 자바스크립트가 브라우저밖에서 사용된다면 존재하지 않습니다. 서버에서 돌아갈 때처럼요. 현대의 브라우저들은 확장된 허가를 얻기 위해서 플러그인/확장모듈 설치를 허용합니다.

## What makes JavaScript unique?

There are at least *three* great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things done simply.
+ Supported by all major browsers and enabled by default.
```

Combined, these three things exist only in JavaScript and no other browser technology.

That's what makes JavaScript unique. That's why it's the most widespread tool to create browser interfaces.

While planning to learn a new technology, it's beneficial to check its perspectives. So let's move on to the modern trends that include new languages and browser abilities.


## Languages "over" JavaScript

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and autoconverting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript, it introduces shorter syntax, allowing to write more precise and clear code. Usually Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing", to simplify development and support of complex systems. It is developed by Microsoft.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps). It was initially offered by Google as a replacement for JavaScript, but as of now, browsers require it to be transpiled to JavaScript just like the ones above.

There are more. Of course even if we use one of those languages, we should also know JavaScript, to really understand what we're doing.

## Summary

- JavaScript was initially created as a browser-only language, but now it is used in many other environments as well.
- At this moment, JavaScript has a unique position as the most widely-adopted browser language with full integration with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
