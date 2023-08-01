# Combobox 접근성

Combobox는 연관된 팝업을 통해 값을 선택할 수 있게 해주는 위젯이다.<br>
팝업의 형태에 따라 값이 제안되어 선택할 수도 있으며, 사용자가 직접 입력하여 제안받거나 입력할 수 있다.<br><br>

### Combobox가 유용한 케이스

- 제안할(허용된) 값이 미리 정의되어 값의 집합을 보유한 경우
- 임의의 값이 허용되지만 가능한 값을 사용자에게 제안하면 유효한 경우

### 팝업 노출

- 팝업은 기본적으로 축소(숨겨져)되어 있으며, "열기" 버튼이 존재하여 팝업의 노출 여부를 제어할 수 있다.
  - `Down Arrow`키를 통해 팝업을 노출할 수 있어야 한다.

## Combobox의 4가지 형태

### 자동 완성 없음

- Combobox를 편집할 수 있다.
- 팝업이 노출될 때 제안되는 값은 Combobox에 입력된 문자와 관계없이 동일하다.

### 수동 선택으로 목록 자동 완성

- 팝업이 노출될 때 제안된 값을 표기한다.
- Combobox를 편집할 수 있는 경우 제안된 값은 Combobox에 입력된 문자와 완전하 일치하거나 논리적으로 일치해야 한다.

### 자동 선택으로 목록 자동 완성

- Combobox를 편집할 수 있다.
- 팝업이 노출되면 Combobox에 입력된 문자와 완전하 일치하거나 논리적으로 일치하는 값을 표기한다.
- 첫 번째 제안이 선택되고 강조 표시를 해야한다.
- 사용자가 다른 제안을 선택하거나 Combobox에서 문자열을 변경하지 않는 한 Combobox가 포커스를 잃으면 자동으로 선택된 제안이 Combobox의 값이 된다.

### 인라인 자동완성

- Combobox를 편집할 수 있다.
- 팝업이 노출되면 Combobox에 입력된 문자와 완전하 일치하거나 논리적으로 일치하는 값을 표기한다.
- 첫 번째 제안이 선택되고 강조 표시를 해야한다.
- 사용자가 다른 제안을 선택하거나 Combobox에서 문자열을 변경하지 않는 한 Combobox가 포커스를 잃으면 자동으로 선택된 제안이 Combobox의 값이 된다.
- 사용자가 입력하지 않은 선택된 제안의 완성된 문자열이 사용자의 커서 뒤로 입력된다. 인라인으로 완성된 문자열은 시각적으로 강조 표시되고 선택된다.

<br>

**_요약_**

`선택하는 자동 완성`: Combobox에 값이 입력되면 논리적으로 해당하는걸 추천하고, 자동 선택되게 할거면 강조
<br>
`인라인 자동 완성`: 자동 선택 자동 완성의 모집합이다. 값이 선택되고 콤보박스에 인라인으로 값이 자동 완성되어 출력

<br><br>

## 접근성 개선

- `<select>`의 `size`속성을 통해 한번에 노출되는 제안 값을 제어할 수 있다
  - 선택 전용 Combobox(텍스트 입력을 지원하지 않는 경우)인 경우 일부 브라우저에서는 HTML `select`요소는`size="1"`를 통해 보조 기술에 해당 정보를 제공할 수 있다.
- Combobox가 편집 가능하다면, 값이 비어 있어도 포커스를 받으면 팝업이 노출되어야 한다
- Combobox가 편집 가능하다면 제안 목록 중 입력 값과 일부 일치한다면 팝업이 노출되어야 한다
- Combobox가 편집 가능하고 목록 자동 완성 형식이 있는 경우 사용자가 입력할 때 팝업이 나타났다가 사라질 수 있습다.
  - 예를 들어 두 개의 문자열을 입력했을때 제안되는 값이 있다면 노출되다가, 다음에 입력한 문자 열을 포함하는 값이 없는 경우 팝업이 닫힌다(인라인 완성 문자열이 있는 경우 사라진다).

<br>

## Keyboard

포커스가 Combobox와 팝업 중 어디에 있냐에 따라 달라진다

### 포커스가 Combobox에 있는 경우

- `Tab`

  > 만약 Combobox에 팝업 노출 버튼이 있다면, 팝업 및 팝업의 내용은 Tab순서에서 제외된다.

- &darr;<br>

  - 팝업이 노출된 경우 포커스를 팝업으로 이동한다.
  - 자동 완성이 되어 있는 경우, 다음 제안의 내용에 포커스가 이동한다.(불가능할 경우 제안 첫 번째 요소에 포커스가 이동)

- &uarr;<br>

  > 팝업이 사용가능한 경우에 제안의 마지막 요소에 포커스가 이동한다.

- `Escape`

  > 팝업이 열려있으면 팝업을 닫는다.<br> 팝업이 닫혀있는 경우 Combobox의 값을 지운다.

- `Enter`

  > Combobox를 편집할 수 있고 팝업에서 자동 완성 제안이 선택된 경우, Combobox에서 값의 끝에 입력 커서를 이동 시키거나, 값에 대한 기본 작업을 수행한다.

- (선택) `Alt + &darr;`

  > 포커스를 이동하지 않고 팝업을 노출시킨다.

- (선택) `Alt + &uarr;`
  > 팝업을 닫고 포커스를 Combobox로 이동한다

### 팝업에 포커스가 있는 경우

- `Enter`

  > 팝업을 닫고 Combobox에 값을 입력한다.<br> 이 후 값의 끝에 입력 커서를 노출시킨다

- `Escape`

  > 팝업을 닫고 콤보박스로 포커스를 이동한다.<br> 만약 콤보상자가 편집 가능하다면 값을 지운다

- &darr;<br>

  > 포커스를 다음 옵션으로 이동시킨다. 포커스가 마지막 옵션에 있는 경우 포커스를 Combobox로 되돌리거나 아무 작업도 수행하지 않는다.

- &uarr;<br>

  > &darr;과 동일하지만 이전 옵션으로 이동시킨다

- &rarr;<br>

  > 콤보박스가 편집 가능한 경우 팝업을 닫지 않고 콤보박스로 포커스를 되돌리고, 입력 커서를 오른쪽으로 한 칸 이동시킨다.<br> 입력 커서가 맨 오른쪽이라면 커서가 커서는 이동하지 않는다.

- &larr;<br>

  > &rarr;과 동일하고 이동 방향만 반대이다.

- (선택) `Home`

  > 첫번째 제안으로 포커스를 이동하고 선택하거나, Combobox가 편집 가능한 경우 포커스를 Combobox로 이동하고 첫번째 문자로 커서를 옮긴다

- (선택) `End`

  > 마지막 제안으로 포커스를 이동하고 선택하거나, Combobox가 편집 가능한 경우 포커스를 Combobox로 이동하고 마지막 문자로 커서를 옮긴다

- (선택) `Backspace`

  > Combobox를 편집할 수 있는 경우 Combobox로 포커스를 되돌리고 커서 앞의 문자를 삭제한다.

- (선택) `Delete`
  > Combobox를 편집할 수 있는 경우 Combobox에 포커스를 옮기고, Combobox에 값이 있는 경우 값을 제거한다.

### 팝업 (그리드)

- (선택) `page down`

  > 작성자가 결정한 행 수만큼 포커스를 아래로 이동시킨다. <br>일반적으로 현재 표시되는 행 세트의 맨 아래 행이 처음 표시되는 행 중 하나가 되도록 스크롤한다.<br> 포커스가 그리드의 마지막 행에 있으면 포커스가 이동하지 않는다.

- (선택) `page up`

  > page down과 동일하지만 방향이 반대이다.

- (선택) `Home`

  > 두 가지 중 하나를 수행한다

  - 포커스가 있는 행의 첫 번째 셀로 포커스를 이동시킨다.
  - Combobox가 편집 가능한 경우 Combobox로 포커스를 되돌리고 첫 번째 문자에 커서를 놓는다.

- (선택) `End`

  > Home과 동일하지만 방향이 반대이다.

- (선택) `Control + Home`

  > 포커스를 첫 번째 행으로 이동시킨다

- (선택) Control + End
  > 포커스를 마지막 행으로 이동시킨다

### 팝업(트리)

- &rarr;<br>

  - 닫힌 노드에 포커스가 있다면 노드를 연다. 이 때 초점과 선택은 움직이지 않는다
  - 열린 노드에 포커스가 있다면 첫 번째 자식 노드로 포커스를 이동하고 선택한다.
  - 포커스가 노드 끝에 있다면 아무 작업도 수행하지 않는다

- &larr;<br>

  > &rarr;과 동일하지만 액션이 반대이다.

- &darr;<br>

  > 노드를 열거나 닫지 않고 포커스 가능한 다음 노드로 포커스를 이동하고 선택 가능한 경우 선택한다

- &uarr;<br>

  > &darr;과 동일하지만 방향이 반대이다.

- `Home`

  > 노드를 열거나 닫지 않고 트리에서 포커스 가능한 첫 번째 노드로 포커스를 이동하고 선택 가능한 경우 선택한다

- `End`
  > Home과 동일하지만 이동 방향이 반대이다

<br><br>

## ARIA Properties

- `role`

  > `combobox` || `listbox`

- `aria-required`

- `aria-haspopup`

  > 만약 팝업의 역할이 listbox가 아닌 다른 역할을 가지고 있다면 aria-haspopup은 당연히 무조건 true이다.<br><br>단, role=combobox라면 암시적으로 aria-haspopup=listbox이다

- `aria-activedescendant`

> 콤보박스의 팝업이 여러 개의 초점 가능한 하위 요소를 포함하는 경우 보조 기술이 초점을 관리하는 데 사용된다.<br>aria-activedescendant는 개별 요소 사이에서 초점을 이동시키는 대신, 컨테이너 요소에 사용되어 현재 활성 요소를 나타낸다.<br> 이를 통해 보조 기술 사용자에게 현재 활성 요소를 알린다.
> <br><br>
> 해당 속성을 사용하면 브라우저는 DOM 초점을 컨테이너 요소나 컨테이너 요소를 제어하는 입력 요소에 유지한다.<br> 그러나 사용자는 aria-activedescendant로 참조된 요소가 초점을 가지고 있는 것처럼 데스크톱 초점 이벤트와 상태를 보조 기술에 전달한다.

```html
<div id="container" role="listbox" aria-activedescendant="item2">
	<div id="item1" role="option">Option 1</div>
	<div id="item2" role="option" aria-selected="true">Option 2</div>
	<div id="item3" role="option">Option 3</div>
</div>
```

- `aria-expanded`

> combobox의 경우 default값은 당연히 false이다

- `aria-selected`

- `aria-autocomplete`

  > `none` | `list` | `both`
  >
  > - none: 팝업이 표시될 때 포함된 제안 값은 Combobox에 입력된 문자와 상관없이 동일
  > - list: 팝업 발생 시 추천 값을 제시 (Combobox를 편집할 수 있는 경우 값은 완전하거나 논리적으로 Combobox에 입력된 문자에 해당)
  > - both: 팝업이 발생하면 콤보박스에 입력한 문자와 완전하거나 논리적으로 일치하는 제안 값을 제시.<br> 위에서 언급했듯 콤보박스가 편집 가능하면 사용자가 입력하지 않은 선택된 제안 부분이 Combobox의 입력 커서 뒤에 인라인으로 나타나고 자동 완성된 문자열은 시각적으로 강조 표시되고 선택된 상태를 가진다.