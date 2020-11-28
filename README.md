# For-people Project
![](https://img.shields.io/badge/license-MIT-brightgreen)
![](https://img.shields.io/badge/HTML-5-orange)
![](https://img.shields.io/badge/css-3-blue)
![](https://img.shields.io/badge/team-awesome-red)
![](https://img.shields.io/badge/documentation-yes-green)

  최신 HTML5와 CSS3로만 구현한 카페 웹사이트
 

## 프로젝트 소개

포피플팀의 프로젝트에 대한 소개와 의의를 말씀드리자면 3주간 배웠던 HTML과 CSS를 통해서 실제로 현업에서 디자인 또는 시안이 주어졌을 경우 FED로서 해야하는 부분을 해결한다는 시나리오를 가정하고 진행하였습니다. 이를 통해서 지난 3주간의 **성과를 알아보고** **git을 활용하는 경험을 축적**하려고 했습니다. 따라서 팀의 방향은 HTML의 마크업과 CSS을 활용한 디자인을 처음부터 끝까지 본인이 맡았던 부분은 해내고 git을 통한 merge와 pull request를 실습하는 방향으로 진행하였습니다. 또한 팀으로서 함께 만들어가는 작품이기에 가장 기초가 되고 3주간 가장 많이 연습했고 강조되었던 **논리적 순서 그리기, 마크업**을 함께 논의하면서 진행하였습니다.


### 사용된 기술
 - HTML5
 - CSS3
 - Git

### 지원 브라우저
- chrome
- IE11
- Firefox
- safari

### 팀원 소개
- [박혜준](https://github.com/margu31)
- [장원준](https://github.com/Wonjuny0804)
- [김지원](https://github.com/iamkjw77)
- [배근아](https://github.com/green9930)
  
## 프로젝트 진행 사항 소개
1. 구상 및 회의
2. 마크업 및 코딩 컨벤션
3. CSS 디자인
4. 코드 리뷰

### 팀의 방향성 설정
- [웹접근성](https://www.w3.org/WAI/fundamentals/accessibility-intro/)
- [SEO](https://en.wikipedia.org/wiki/Search_engine_optimization)
- [git 활용]()
- 유저 friendly

### 클래스 네이밍
 본 프로젝트에서는 각 클래스네이밍에 [BEM표기법](http://getbem.com/)을 사용하였다. 
### CSS 디자인

### 코드 리뷰
- CSS 모듈화
- 중복코드 삭제 및 코드 간소화
- 주석처리
- lighthouse 검사 및 피드백을 통한 수정
- 배포용 버전 디렉토리 생성

### 팀원별 개발 과정

#### 장원준

1. sign up 페이지
전체적인 팀의 개발 방향을 정하고나서 signup페이지를 마크업하기 시작했다. 마크업은 다음과 같은 순서로 진행하였다. 
      1. 논리적인 흐름구상
      2. 전체적인 페이지의 흐름, 용도를 파악하며 html tag를 결정
      3. 팀에서 정한 컨벤션으로 클래스 이름을 부여
      4. 복수 클래스가 있는지 확인
      5. html문서로 작성
      6. css 디자인

sign up페이지에서 어려웠던 부부은 많이 있었지만 가장 기억에 남는 부분은 크게 두 가지가 있다.
먼저 선택적 정보 동의 체크 버튼을 시안대로 디자인하는 과정에서 발생했던 문제였다. 

**문제점**
시안에서는 체크박스가 체크되었을때 시안 체크박스의 전후 요소의 색이 다르도록 설정되어 있었다. 
이를 해결하려고 span요소를 생성하고 span::after를 생성해서 두 요소를 시안과 같은 디자인으로 만들었다. 그래서 전후 요소에 같은 색을 주고 `opacity`를 시안대로 0.6으로 설정하였다. 그랬더니 span과 span::after모두 같은 색이 되었다. 아무리 색을 다르게 줘도 같은 색을 나타낼 뿐이었다. 
```css
background: #abcd3;
opacity: .6;
```
![](./images/md/check-switch-before.png)

**해결방법**
opacity는 속성 값으로 들어간 요소의 자식요소에게 상속되는 속성이다. 그렇기 때문에 자식요소가 다른 opacity값을 가져도 그 값은 들어가지 않는다. 따라서 opacity속성을 삭제하고 두 요소에 서로 다른 색상을 주는 방법도 있지만. opacity 속성과 동일한 rgba(0,0,0,0.6)으로 색 속성을 바꿔주면된다. rgba에서 마지막 알파채널을 통해서 투명도를 지정할 수 있고 이는 0과 1사이의 값을 주면된다. 자식 요소에 상속되서 생기는 문제점을 해결할 수 있다.
```css
background: rgba( 0,0,0, 0.6);
``` 
![](./images/md/check-switch-after.png)

두번째 발생했던 문제는 placeholder에 발생했던 문제였다. placeholder는 그 특성상 보조기기에서 읽어주지 않고 또한 input요소에 focus를 주고 입력함과 동시에 힌트가 사라지는 문제가 존재했다. 이러한 부분은 저시력자 또 힌트가 너무 긴경우 어려움을 줄 수 있어서 이 부분을 해결하려고 했고 실제 다른 회사들은 이 문제를 어떻게 해결했는지 벤치마킹해보았다. 

그러한 회사 중 하나가 바로 apple인데 apple은 다음과 같이 문제를 해결한 듯 하다. 
![](./images/md/placeholder-apple.png)

상단에서 보이는 것처럼 마우스 포커스가 올라가면 안에 있던 '힌트' 또는 '레이블'이 상부로 작아지면서 이동하는 것을 볼 수 있다. 이렇게 해줌으로서 시각적인 힌트를 사라지지 않고 계속해서 사용할 수 있으며 또한 시각장애인 분들이 input요소에 대한 힌트를 들을 수 있게 해줄 수 있다.

#### 배근아  
1. 메인 페이지 section2, 3, 6, 7 HTML, section3 CSS      
  
  **마크업 순서**  
  (1) 논리적인 흐름 구상  
  (2) 그림으로 HTML 초안 작성 및 tag 결정  
  (3) 팀에서 정한 컨벤션으로 클래스 이름 부여  
  (4) HTML 작성  
  (5) CSS 디자인  
    
  **issues**  
  (1) section2의 HTML/CSS  
    [section2 REVIEW](https://www.notion.so/green9930/Review-01-Section-02-a1096a88198949aca8c0c76ebccbb5dd)  
    
    <초안>  
    ```html
    <section class="recommend__multi">
    ...
    </section>
    <section class="recommend__euid">
    ...
    </section>
    <button type="button" class="btn-prev" title="이전 페이지">prev</button>
    <button type="button" class="btn-next" title="다음 페이지">next</button>
    ```  
      
    <최종안>  
    ```html
    <section class="recommend__multi">
      <button type="button" class="multi__btn-prev" title="이듬 블랜디드 이전 페이지">prev</button>
      <button type="button" class="multi__btn-next" title="이듬 블랜디드 다음 페이지">next</button>
    </section>
    <section class="recommend__euid">
      <button type="button" class="euid__btn-prev" title="이듬 블랜디드 이전 페이지">prev</button>
      <button type="button" class="euid__btn-next" title="이듬 블랜디드 다음 페이지">next</button>
    </section>
    ```  
    처음 구상할 때는 컨텐츠 양 옆에 위치한 버튼이 HTML에서 한 번만 들어가는 방식이었지만 논리 구조를 다시 고민하며 마크업을 수정했다.  
    시각적 차이는 없으나 앞선 방식은 논리적으로 '멀티 캠퍼스' 섹션을 지나쳐 '이듬 블랜디드'의 컨텐츠를 확인한 후 버튼이 있기 때문에 웹 접근성 측면에서 바람직하지 못한 구성이었다. 따라서 '멀티 캠퍼스' 섹션과 '이듬 블랜디드' 섹션 모두에게 `<button>` 태그를 넣었다.  
    학습 초기에는 눈앞에 보이는 요소만 고려해서 마크업을 짰지만 점점 논리적인 구조를 먼저 생각하고 있음을 깨달은 경험이었다.  
    
  (2) section3의 CSS  
    [section3 REVIEW](https://www.notion.so/green9930/Review-02-Section-03-c12365a125ba46e488980d30bcf08356)  
    
    전체 섹션에 padding을 줬음에도 브로슈어 박스가 그 padding을 뚫고 나가는 문제가 발생했고, 브로슈어 박스에 넣은 배경 이미지나 화살표의 위치를 조정해도 해결되지 않았다. 처음엔 임시로 `<a>`의 height를 고정했고, 나머지 파트 CSS를 끝낸 뒤 다시 코드를 살펴봤을 때 브로슈어 박스 내부에 padding을 줬다는 걸 발견했다.    
    단순한 실수였지만 원인을 빨리 찾지 못해 해결에 난항을 겪었던 부분이었다.  
    
  (3) section6의 HTML  
    [section6 REVIEW](https://www.notion.so/green9930/Review-03-Section-06-9533c81145444f9784ab19c01a07c02a)  
    
  (4) section7의 HTML  
    [section7 REVIEW](https://www.notion.so/green9930/Review-04-Section-07-a70870b7417641b8b04441f8e459ca34)  
  
2. 발표 및 대본 준비  
발표 방향을 기획하고 프레젠테이션 자료를 준비했다.  
방향 설정 단계에서 가장 많이 고려한 부분은 '이 프로젝트를 하게 된 이유'였다. 우리가 학습했던 HTML/CSS만을 이용한 페이지 구현이었기 때문에 완성도는 떨어질 수밖에 없었다. 따라서 결과물보단 우리의 프로젝트 실행 과정과 그 과정 중에 겪었던 어려움과 해결방법 위주의 발표 진행이 가장 적합할 것으로 판단했다.  
또한 팀원들의 발표 대본 작성을 도왔다. 대본 초안 작성을 돕고 최종 대본 수정으로 각자의 발표 내용이 팀 발표라는 큰 틀에서 형식상의 일관성을 유지하도록 했다.  

3. 느낀점  
한 단어로 정리하자면 미숙함이다.  
강사님의 수업과 달리 동료들과 함께 고민하고 markup부터 디자인까지 직접 구현해보니 부족함을 많이 느꼈다. 예상한 대로 코드가 구현되지 않으면 이유를 곧바로 찾지 못했고, git이나 figma 사용도 익숙지 않아 당황스러운 상황이 생기기도 했다.  
그리고 동적으로 움직이는 상황을 가정하면서 HTML/CSS를 완성해야 한다는 점이 답답하기도 했는데 완벽한 웹페이지 구성에 욕심이 생기면서 향후 학습하게 될 JavaScript에 대한 갈증도 많이 느끼게 해준 계기가 된 것 같다.  


### 마치며

- 접근성 - 사실 컴공4년을 다니면서 한번도 들어보지 못했던 개념이다. 접근성은 단연 개발자에게 있어서 중요한 고려 요소이다. 기술이 발전함에 따라 많은 사람들이 그 혜택을 누리지만 또 그것을 누리지 못하는 이들이 있고 그들도 이 기술과 웹이라는 세상에 접근할 수 있도록 돕는 연결다리 역할을 하는 것이 개발자의 역할이라는 생각이 들었다. 시대가 지나고 기술이 변해도 접근성은, 더 나아가 기술자로서 세상을 더욱 연결되게해주고 서로가 더 가까워질 수 있도록 돕는 역할은 변하지 않을 것이라고 생각하게된 굉장히 중요한 부분이었다. 
- 퍼포먼스 - 결국 사용자에게 더 쾌적한 환경을 제공하기 위해서 최적화, 또 preload등을 활용했는데 이번 프로젝트는 이러한 렌더링과 서비스의 작동 퍼포먼스에 대해서도 계속 고민하게 만들었다. 
- 협업 - 깃을 통해서 처음으로 협업했던 이번 프로젝트는 git이 얼마나 유용한지 알게해줬고 팀장으로서 충돌이 났을때 해결하는 방법을 익히는 아주 유익한 시간이었다. 다음부터는 `git flow feature start`를 정말 작은 모듈 단위로 해야겠다는 생각이 들었고 협업을 할때도 팀원들에게 일정 시간이 지나면 선 pull 후 commit,push를 하도록 요청해야한다는 **중요한** 교훈을 깨닫게해준 프로젝트였다.