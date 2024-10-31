# Project

Vue.js를 이용해서 만드는 간단 영화 App

- VS Code로 개발
- JavaScript 사용
- Vue 3 버전 사용
- 컴포넌트로 분리
- 기본 Vue 문법 사용
- 검색, 좋아요, 상세보기, 전체 보기 등 구현

---

# Tech Stack
| Tech         | Content                                                                                                                                                                                                                     |
| :----------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Language**  |  ![JavaScript](https://img.shields.io/badge/JavaScript-%23323330.svg?style=flat&logo=javascript&logoColor=white)  |
| **Framework** | ![Vue.js](https://img.shields.io/badge/-Vue.js-green?logo=vue.js&logoColor=white) ![HTML](https://img.shields.io/badge/-HTML5-E34F26.svg?style=flat&logo=html5&logoColor=white) ![CSS](https://img.shields.io/badge/-CSS3-1572B6.svg?style=flat&logo=css3&logoColor=white)|
| **IDE**       |![VScode](https://img.shields.io/badge/VScode-blue?logo=vscode&logoColor=white) |
|   **Tools**   | ![Notion](https://img.shields.io/badge/-Notion-000000?logo=notion&logoColor=white) ![Git](https://img.shields.io/badge/-Git-F05032?logo=git&logoColor=white)          |

---
|![image](https://github.com/user-attachments/assets/3a2168b4-0643-4f88-a22f-4acd59026ae4)|![image](https://github.com/user-attachments/assets/9a76159d-004b-47a3-b15d-eda23f7c8303)|![image](https://github.com/user-attachments/assets/2e83f2b5-6bf2-4e66-8f55-97c38007d662)|
|:--------:|:----------:|:-------:|

---
# Vue 기본 문법

### template 섹션
- Vue 컴포넌트의 HTML 구조를 정의
- 화면에 표시될 요소들을 작성
- **Vue 2.x**에서는 템플릿 내에 단일 루트 엘리먼트가 필요
  - 하나의 **`div`** 또는 다른 HTML 요소로 감싸져 있어야 했음
  - 루트 엘리먼트가 없거나 여러 개의 루트 엘리먼트가 있을 경우, Vue 2.x는 오류 발생
- **Vue 3.x**에서는 **`Fragment`** 기능이 추가
   - 템플릿 내에서 루트 엘리먼트가 없어도 오류가 발생하지 않음
   - 여러 개의 루트 엘리먼트 사용 가능
   - 더 유연한 템플릿 구성이 가능
    
### script 섹션
- Vue 컴포넌트의 로직과 데이터를 정의
- 컴포넌트의 동작과 상태를 관리
- JavaScript 코드를 포함
- 컴포넌트의 데이터, 메서드, 라이프사이클 훅, 컴포넌트 간 통신을 관리
- export default: 컴포넌트를 외부에서 사용할 수 있도록 내보냅니다.
- data(), methods, computed, props, components 등 Vue 컴포넌트의 다양한 옵션을 설정

### style 섹션
- Vue 컴포넌트의 스타일을 정의
- HTML 요소들이 어떻게 보여질지를 결정
- CSS 코드가 포함
- 컴포넌트 내에서 사용되는 요소들의 스타일을 정의
- <style>태그: 전역 스타일을 적용 가능
- scoped 속성을 사용하면 해당 컴포넌트에만 적용되는 로컬 스타일을 정의 가능
- CSS 전처리기(SCSS, LESS 등)를 사용 가능

### data()
  ```
  data(){
	return{ 
	// 오브젝트 형태(키와 값)로 반환
	}:
}
or
data:()⇒{
}
  ```

### 변수 사용
`{{ 변수명}}`

### v-text
- HTML 요소의 텍스트 콘텐츠만을 설정
- 태그 안에 다른 HTML 요소나 텍스트를 삽입하면 오류가 발생

### v-model
- 직접 input 태그의 값을 바꿔도 적용됨
- 상태 관리가 되고 있음
- 복잡한 JS 코드 없이 손 쉽게 데이터를 업데이트 하고 공유하는 것끼리 연결 가능

### v-html
- 태그 자체를 가져와서 보여주고 싶을 경우 사용
- 확실하게 믿을 수 있는 경우에만 사용하기
    - **보안 문제**
        - HTML을 직접 삽입
        - 사용자 입력을 HTML로 렌더링할 때 XSS(교차 사이트 스크립팅) 공격에 취약할 수 있음
    - **HTML 인젝션**
        - 외부 소스에서 HTML 콘텐츠를 삽입할 때는 반드시 신뢰할 수 있는지 확인 필수
        - 불필요한 HTML 태그나 악성 스크립트가 포함되어 있을 수 있기 때문에 주의
    - **성능 문제**
        - 대량의 HTML 콘텐츠를 **`v-html`**로 삽입하면 렌더링 성능에 영향을 줄 수 있음
- 그냥 사용하면 String으로 인식됨

### v-bind
- 동적으로 연결

### v-if
- 조건이 참일 때만 요소를 렌더링
- 조건이 거짓일 때는 요소가 DOM에서 제거
- 새롭게 생성할 경우 사용
- 같은 레벨(한 부모안에 형제)로 이어져있어야 함
    - 조건문 안에 다른 태그가 들어가면 에러 발생

### v-show
- 조건에 따라 요소의 **`display`** CSS 속성을 변경
- 요소는 항상 DOM에 존재하지만, 조건이 거짓일 때는 숨겨짐

### v-for
- 배열이나 객체의 각 항목을 반복하여 DOM 요소를 렌더링
- 반복할 데이터와 각 항목에 대한 키를 지정해야 함
- **키 속성 (`:key`)**
    - **`v-for`**를 사용하여 반복적으로 생성되는 요소의 고유성을 식별하기 위해 사용
    - 각 반복 항목에 대해 고유한 값을 가짐
    - 이 키를 사용하여 어떤 항목이 변경되었는지, 추가되었는지, 삭제되었는지를 추적
    - **장점**
        - **성능 최적화**
            - **`key`**를 사용하여 가상 DOM과 실제 DOM 간의 차이를 더 효율적으로 계산할 수 있음
            - 불필요한 DOM 업데이트를 방지하고, 렌더링 성능을 향상
        - **안정성**
            - 동일한 컴포넌트가 동일한 데이터를 가지더라도, **`key`**를 통해 Vue는 각 항목의 위치와 상태를 정확히 추적할 수 있음
            - 데이터 변경 시에 예상치 못한 UI 문제를 방지
- v-if와 v-for는 함께 사용할 수 없음

### Props
- 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 방법
- 읽기 전용이며, 자식 컴포넌트는 부모 컴포넌트로부터 받은 값을 변경할 수 없음
  ```
  props: {
      type: String,       // 변수명: 데이터의 타입
    },
  ```

### Emit
- 자식 컴포넌트가 부모 컴포넌트로 이벤트를 발생시킬 때 사용
- 자식 컴포넌트는 부모 컴포넌트에서 정의된 메소드를 호출할 수 있음
  `$emit(커스텀이벤트 명, 선택 데이터)`
