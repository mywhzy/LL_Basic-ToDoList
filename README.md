## 이번 프로젝트는 *JavaScript 복습 -> TypeScript 학습*을 위한 _ToDoList_ 기본 CRUD 구현하기입니다.

---

### _HTML + CSS + TS (->JS)_ 만을 통한 기본적인 웹 프로그래밍을 진행합니다.

---

#### **현재까지 구현된 기능**

**1. 할 일 _추가_**  
**2. 할 일 _수정_ (🖋버튼 누른 후 엔터 누르면 적용)**  
**3. 할 일 _완료 표시_ (할 일 텍스트 더블 클릭 시 적용)** _=> classList.toggle 이용_  
**4. 할 일 _삭제_ (✖버튼)**  
**5. _남은 할 일 개수_ 나타내기**

---

#### **To Do List의 기본 기능에 충실하기 위해 위와 같은 5가지 기능을 구현하였으며**

#### **1. 해야 할 일을 입력하고 2. 작성한 할 일을 확인하며**

#### **3. 완료한 일 분류와 4. 필요 없는 경우 삭제하고**

#### **5. 내용에 수정이 필요한 경우 업데이트할 수 있게 하였습니다.**

#### **6. 더불어 오늘 날짜와 남은 할 일 개수를 보여주며 사용자의 편의를 더해주었습니다.**

---

```
├─ .gitignore // /node_modules, /dist(컴파일된 js파일용 폴더)
├─ index.html
├─ src
│  ├─ date.ts // show today's date
│  └─ todolist  // control todolist items
│     ├─ completeItem.ts  // complete to do item
│     ├─ countingItem.ts  // counting to do item
│     ├─ createItem.ts  // create to do item
│     ├─ deleteItem.ts  // delte to do or done item
│     └─ updateItem.ts  // update to do item
├─ style.css
└─ yarn.lock, package.json, tsconfig.json, README.md ...
```

**LiveServer를 통해 실행 가능합니다**

---

### 커밋 컨벤션

| 커밋명   | 내용                                |
| -------- | ----------------------------------- |
| feat     | 기능 개발                           |
| fix      | 버그 수정                           |
| refactor | 코드 또는 폴더 구조 리팩토링        |
| style    | 코드 변경 없는 수정                 |
| design   | css와 같은 스타일 및 ui 디자인 변경 |
| docs     | 단순 문서(read me) 수정             |
| comment  | 필요한 주석 추가 및 변경            |

---

5번 기능의 경우 완료된 할 일 ul영역을 따로 분리하여 구현했습니다.  
_완료된 할 일은 수정이 불가하며 완료 해제 및 삭제만 가능_ 합니다.

---

**피드백 반영 수정된 부분**

1. 중복 코드 최소화 (함수를 최대한 많이 활용해 중복 코드 분리)

- 각 list item에 대한 update, delete 버튼 생성 함수
- add list item 함수 (create list item)
- 할 일 입력창 빈값인지 check하고 list에 insert해주는 함수
- 할 일 완료 여부 확인 함수
- update 버튼 toggle 함수
- remove list item 함수

2. 1번과 같은 함수 분리로 event처리 시 다른 event에 영향받지 않고 원하는 동작만 가능하게 함

==> 중복 코드가 상당히 많음을 인지하고 함수를 생성해 중복 코드 최소화와 event내에 기능 직접 명시가 아닌 함수 호출 구조로 변경(아직 update는 제외,,^^)
함수로 관리 시 동일 기능 코드의 수정에서 한 번의 수정으로 모두에게 예외없이 동일한 적용이 가능하며 event 종속 방지됨

3. countTodo()에서 listitem개수 세는 방식 "querySelectorAll"로 수정해 다른 엘리먼트가 추가돼도 해당 엘리먼트만 카운팅하도록 변경

4. complete시의 list item에서 update 버튼을 children이 아닌 querySelector로 조작하게 변경

=>문서 자체에서 자식 노드에 변경이 있을 시 의도하지 않은 결과가 초래될 수 있음. querySelector를 이용해 특정 자식 노드 선택을 id값을 통해 할 수 있게 함

5. update to do 시 add to do와 동일하게 빈 값 허용X

6. 기능별 파일 분리 및 폴더 구조 변경

---

수정, 공부 필요한 부분

- update 부분 함수로 분리(event함수 간략화) / parentnode사용과 childnode 사용 다른 방식으로 접근해 줄이기

- typeScript로 변환 -> 타입 단언 지양 but 어떻게 선언? , 어떤 type으로 지정해야하나? 의 어려움

- delete시 parentnode 사용 지양 방식으로 변경

- webpack 적용

---
