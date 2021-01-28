---
template: overrides/main.html
---
# 프로그래밍 시작하기

## 코딩 컨벤션 (Coding Convention)

Python은 PEP (Python Enhance Proposal) 8을 따른다.

### Code lay-out

- [x] 들여쓰기는 공백 4칸을 권장한다.
- [x] 한 줄은 최대 79자까지
- [x] 최상위(top-level) 함수와 클래스 정의는 2줄씩 띄어 쓴다.
- [x] 클래스 내의 메소드 정의는 1줄씩 띄어 쓴다.



### Whitespace in Expressions and Statements

- [x] 다음과 같은 곳의 불필요한 공백은 피한다. 
	- 대괄호([])와 소괄호(())안
	- 쉼표(,), 쌍점(:), 쌍반점(;) 앞
- [x] 키워드 인자와 인자의 기본값의 "=" 는 붙여 쓴다.

### Comments
- [x] 코드와 모순되는 주석은 없느니만 못합니다. 항상 코드에 따라 갱신해야 합니다.
- [x] 불필요한 주석은 달지 마세요.
- [x] 한 줄 주석은 신중히 다세요.
- [x] 문서화 문자열(Docstring)에 대한 컨벤션은 PEP 257을 참고하세요.


```
  
    def add_two_numbers(number1, number2):
      """Returns the sum of two numbers
      Args:
          number1 (int): First number to add
          number2 (int): Second number to add
      Returns:
          int: Sum of `number1` and `number2`
```

### Naming Conventions

- [x] 변수명에서 _(밑줄)은 위치에 따라 다음과 같은 의미가 있습니다.
	-  _single_leading_underscore : 내부적으로 사용되는 변수를 일컫습니다.
	-  single_trailing_underscore_ : 파이썬 기본 키워드와 충돌을 피하려고 사용합니다.
	-  __double_leading_underscore : 클래스 속성으로 사용되면 그 이름을 변경합니다. (ex. FooBar에 정의된 __boo는 _FooBar__boo로 바뀝니다.)
	-  __double_leading_and_trailing_underscore__ : 마술(magic)을 부리는 용도로 사용되거나 사용자가 조정할 수 있는 네임스페이스 안의 속성을 뜻합니다. 이런 이름을 새로 만들지 마시고 오직 문서대로만 사용하세요.
- [x] 소문자 L, 대문자 O, 대문자 I는 변수명으로 사용하지 마세요. 어떤 폰트에서는 가독성이 굉장히 안 좋습니다.
- [x] 모듈(Module) 명은 짧은 소문자로 구성되며 필요하다면 밑줄로 나눕니다.
	- 모듈은 파이썬 파일(.py)에 대응하기 때문에 파일 시스템의 영향을 받으니 주의하세요.
	- C/C++ 확장 모듈은 밑줄로 시작합니다.


```

      (good) import modulename
      (bad) import ModuleName
      (bad) import module_name
```

- [x] 클래스 명은 카멜케이스(CamelCase)로 작성합니다.
	- 내부적으로 쓰이면 밑줄을 앞에 붙입니다.
	- 예외(Exception)는 실제로 에러인 경우엔 "Error"를 뒤에 붙입니다.

```

      (good) class CamelCase(object):
      (bad) class mixedCase(object):
      (bad) class snake_case(object):
```

- [x] 함수명은 snake_case로, 소문자로 구성하되 필요하면 밑줄로 나눕니다.
	- 대소문자 혼용은 이미 흔하게 사용되는 부분에 대해서만 하위호환을 위해 허용합니다.

```

      (good) def python_function_name(arg1, arg2):
      (bad) def PythonFunctionName(arg1, arg2):
      (bad) def pythonFunctionName(arg1, arg2):
```

- [x] 인스턴스 메소드의 첫 번째 인자는 언제나 self입니다.
- [x] 클래스 메소드의 첫 번째 인자는 언제나 cls입니다.
- [x] 메소드명은 함수명과 같으나 비공개(non-public) 메소드, 혹은 변수면 밑줄을 앞에 붙입니다.
- [x] 서브 클래스(sub-class)의 이름충돌을 막기 위해서는 밑줄 2개를 앞에 붙입니다.
- [x] 상수(Constant)는 모듈 단위에서만 정의하며 모두 대문자에 필요하다면 밑줄로 나눕니다.

### Programming Recommendations


- [x] 코드는 될 수 있으면 어떤 구현(PyPy, Jython, IronPython등)에서도 불이익이 없게끔 작성되어야 합니다.
- [x] None을 비교할때는 is나 is not만 사용합니다.
- [x] 클래스 기반의 예외를 사용하세요.
- [x] 모듈이나 패키지에 자기 도메인에 특화된(domain-specific)한 기반 예외 클래스(base exception class)를 빌트인(built-in)된 예외를 서브클래싱해 정의하는게 좋습니다. 이 때 클래스는 항상 문서화 문자열을 포함해야 합니다.


```

    class MessageError(Exception):
      """Base class for errors in the email package."""
```

- [x] raise ValueError('message')가 (예전에 쓰이던) raise ValueError, 'message' 보다 낫습니다.
- [x] 예외를 except:로 잡기보단 명확히 예외를 명시합니다.(ex. except ImportError:
- [x] try: 블록의 코드는 필요한 것만 최소한으로 작성합니다.
- [x] string 모듈보다는 string 메소드를 사용합니다. 메소드는 모듈보다 더 빠르고, 유니코드 문자열에 대해 같은 API를 공유합니다.
- [x] 접두사나 접미사를 검사할 때는 startswith()와 endwith()를 사용합니다.
- [x] 객체의 타입을 비교할 때는 isinstance()를 사용합니다.
- [x] 빈 시퀀스(문자열, 리스트(list), 튜플(tuple))는 조건문에서 거짓(false)입니다.
- [x] 불린형(boolean)의 값을 조건문에서 ==를 통해 비교하지 마세요.


## 버전 명명 규칙

### 파이프라인 버전
파이프라인을 개발하는데 있어서 파이프라인의 버전 을 확정하고, 해당 파이프라인이 적용되는 패널 을 우선 정의한다. 파이프라인의 파이프라인의 요구사항, 개발 계획, 파이프라인 개발에 있어서 잠재적인 위험요소를 구분하는 위험경영, 만들어진 파이프라인의 검증 과 최종적인 파이프라인에 대해 전반적인 기술을 한다.

### Semantic Versioning  :octicons-heart-fill-24:{: .tx-heart }
Major, Minor 그리고 path의 의미를 담고 있는 버전 명명법 [Semantic Versioning][1] 을 사용하여 파이프라인의 버전을 관리합니다.

[![Creating your site][2]][2]

   [1]: https://semver.org/lang/ko/
   [2]: assets/screenshots/version.png

- [x] 주 버전 (Major version)  
	- Increment for __backwards-incompatible__ changes.
	- 이전 버전과 호환이 안 되는 변경
- [x] 개선 버전 (Minor version)  
	- Increment for __new features__.
	- 이전 버전과 호환되는 기능 추가
- [x] 업데이트 버전 (Patch version)
	- Increment for __bug fixs__.
	- 이전 버전의 버그를 수정


!!! warning "파이프라인 버전"

	DNA 파이프라인의 최신 버전은 v1.4로 fusion 탐지를 위한 GRIDSS가 추가되었으며, Software에는 DNA 파이프라인 버전 v1.3이 적용되어 있다.   


## 개발을 위한 준비 사항


### 개발에 적합한 IDE 또는 문서 편집기 선택

* 자바 개발자라면 [IntelliJ IDEA][3] 를 추천합니다.
* 파이썬 개발자라면 [Visual Studio Code][4] 나 [Sulime Text][5] 를 추천합니다.
* 편집기와 git을 연동할 수 있으면 편리합니다.

	[3]: https://www.jetbrains.com/ko-kr/idea/
	[4]: https://code.visualstudio.com/
	[5]: https://www.sublimetext.com/

### 계정 생성하기

* [Github][6] 에 계정을 생성합니다.
* 관리자에게 자신에게 할당된 [회사의 github][7]  프로젝트의 권한을 요청합니다.
* 관리자에게 개발서버의 계정 발급을 요청합니다.
* 필요시 관리자에게 __GUI Client__ 설치 파일을 요청합니다.

	[6]: https://github.com/
	[7]: https://github.com/ngenebio

## Github을 이용한 개발

[![github][8]{: width=50%}][8]

   [8]: assets/screenshots/github.png
   

### 원격 저장소에서 로컬 저장소로 가져오기


* 자신에게 권한이 부여된 git repository (upstream)를 fork 한다.

[![fork][9]][9]

   [9]: assets/screenshots/fork.png

* fork된 저장소(origin)를 로컬로 가져와 (clone) 작업을 하면 된다.[^1]

  [^1]:
    Pull from upstream changes to original

```

    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git > git clone https://github.com/hongiiv/CLNANN.git
    'CLNANN'...
    remote: Enumerating objects: 3, done.
    remote: Counting objects: 100% (3/3), done.
    remote: Compressing objects: 100% (3/3), done.
    remote: Total 76 (delta 0), reused 1 (delta 0), pack-reused 73
    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git > cd CLNANN
    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN > > master > git remote -v
    origin  https://github.com/hongiiv/CLNANN.git (fetch)
    origin  https://github.com/hongiiv/CLNANN.git (push)
```

### 기존 원격 저장소(upstream) 연결


* 기존에 fork한 프로젝트의 변경사항을 확인(pull) 가능하도록 한다.
* 이제 pull을 하면 원격 저장소(upstream)의 변경 사항도 반영된다.
* 반영된 결과를 나의 수정사항과 함께 나의 원격 저장소(origin)에 반영하면 된다. 
* 내 repository(origin)에 upstream을 알려줌 (git remote add upstream {remote_address})

```

    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN >> master > git remote add upstream https://github.com/ngenebio/CLNANN.git
    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN >> master > git remote -v
    origin  https://github.com/hongiiv/CLNANN.git (fetch)
    origin  https://github.com/hongiiv/CLNANN.git (push)
    upstream  https://github.com/ngenebio/CLNANN.git (fetch)
    upstream  https://github.com/ngenebio/CLNANN.git (push)
```

* 코드를 작성한 후
* 코드를 의미있는 단위로 쪼개서 commit (git commit)
* 변경 사항이 upstream에 존재할 수 있기 때문에 upstream을 fetch (git fetch upstream)
* fetch 명령은 타겟으로 지정한 리포지토리의 변경내역을 로컬로 가지고 와서 그 내역들을 HEAD라는 특수한 branch에 담는다.
* commit들을 모아서 push(git push origin HEAD)

```

    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN > > master > vi README.md
    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN > > master ● > git add README.md
    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN > > master ✚ > git commit -m 'hi there'
    [master c05bb7b] hi there
     1 file changed, 1 insertion(+), 1 deletion(-)
    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN > > master > git fetch upstream
    https://github.com/ngenebio/CLNANN URL에서
     * [새로운 브랜치]   dev        -> upstream/dev
     * [새로운 브랜치]   master     -> upstream/master
    (base)  hongchangbum@Hongui-MacBook-Pro > ~/git/CLNANN > > master > git push origin HEAD
    오브젝트 나열하는 중: 5, 완료.
    오브젝트 개수 세는 중: 100% (5/5), 완료.
    Delta compression using up to 12 threads
    오브젝트 압축하는 중: 100% (3/3), 완료.
    오브젝트 쓰는 중: 100% (3/3), 290 bytes | 290.00 KiB/s, 완료.
    Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
    To https://github.com/hongiiv/CLNANN.git
       fae2eab..c05bb7b  HEAD -> master
```

### Pull request

_만약 나에게 권한은 없지만 기여하고 싶은 프로젝트가 있다면 clone 이전에 먼저 해당 프로젝트를 fork해오는 작업이 필요합니다. fork는 다른 사람의 저장소를 가져와 내 저장소를 만드는 기능입니다.작업 후 add와 commit, push까지 하여 커밋을 남기면 이는 fork한 내 레포지토리에만 반영될 뿐, 원본 레포지토리에는 아무런 영향을 줄 수 없습니다. 당연합니다. 권한 없는 사람이 누구나 Remote Repository를 변경할 수 있다니, 얼마나 혼란하겠습니까. 따라서 우리는 자신의 개인 저장소에서 작업한 후 이 작업을 원본 레포지토리에 반영해 달라고 요청할 수 있습니다. 이 과정이 바로 ‘Pull Request’입니다. 원본 레포지토리 관리자는 이를 확인하고 수락하여 해당 커밋을 원본 레포지토리에 merge하거나 거절하는 등의 작업을 할 수 있습니다. 자신이 작성한 Pull Request가 받아들여졌는지에 대한 여부는 원본 레포지토리의 Pull requests 탭에서 확인할 수 있습니다._

위의 내용을 다시 한 번 요약해보자면:

- “fork”를 통해 원본 레포지토리를 가져와 내 레포지토리를 만든다.
- “clone”을 통해 fork한 내 레포지토리를 로컬에 가져온다.
- 로컬에서 작업 후 “add” -> “commit” -> “push”를 통해 내 레포지토리에 작업내용을 업로드한다.
- “Pull Request”를 통해 내 작업내용을 원본 레포지토리에 반영해달라고 요청한다. :material-new-box:

[![pull request][10]][10]

   [10]: assets/screenshots/pull_request.png

[:octicons-heart-fill-24:{: .tx-heart } &nbsp; Join our <span class="tx-insiders-count"></span> awesome sponsors][5]{: .md-button .md-button--primary .tx-insiders-button }

<div class="tx-insiders-container" markdown="1" hidden>
  <div class="tx-insiders-list"></div>
  _If you sponsor publicly, you're automatically added here with a link to
  your profile and avatar to show your support for Material for MkDocs.
  Alternatively, if you wish to keep your sponsorship private, you'll be a 
  silent +1. You can select visibility during checkout and change it 
  afterwards._
</div>

<script>
  fetch("https://gpiqp43wvb.execute-api.us-east-1.amazonaws.com/_/").then(function(e){return e.json()}).then(function(e){var t=document.querySelector(".tx-insiders-list"),n=0;for(var o of e.sponsors)if("PUBLIC"===o.type){var s;(s=document.createElement("a")).href=o.url,s.title="@"+o.name,s.className="tx-insiders-list__item",t.appendChild(s);var r=document.createElement("img");r.src=o.image,s.appendChild(r)}else n++;(s=document.createElement("a")).href="https://github.com/sponsors/squidfunk",s.title="[private]",s.innerText="+"+n,s.className="tx-insiders-list__item tx-insiders-list__item--private",t.appendChild(s),document.querySelector(".tx-insiders-count").innerText=e.sponsors.length,document.querySelector(".tx-insiders-container").removeAttribute("hidden"),document.querySelector('.tx-insiders-total').innerText=" – $ "+e.total.toString().replace(/(\d)(?=(\d{3})+(?!\d))/g, "$1,")}).catch(console.log);
</script>