# 키친포스

## 요구 사항

### 상품
- [ ] 상품 이름과 가격을 받아서 상품정보를 등록할 수 있다.
  - [ ] 상품 가격이 입력되지 않거나 0 미만이면 예외처리한다.
- [ ] 등록된 전체 상품 정보를 조회할 수 있다.


### 메뉴 그룹
- [ ] 메뉴 그룹 이름을 받아서 메뉴 그룹 정보를 등록할 수 있다.
- [ ] 등록된 전체 메뉴 그룹 정보를 조회할 수 있다.


### 메뉴
- [ ] 메뉴 이름, 가격, 메뉴 그룹 ID, 메뉴 상품 리스트를 받아서 메뉴 정보를 등록할 수 있다.
  - [ ] 메뉴 가격이 입력되지 않거나 0 미만이면 예외처리한다.
  - [ ] 메뉴 그룹 ID가 존재하지 않는 것이면 예외처리한다.
  - [ ] 각 메뉴 상품들의 (가격 * 수량) 값의 합보다 메뉴 가격이 높으면 예외처리한다.
  - [ ] 메뉴와 해당하는 메뉴 상품 정보들을 자동으로 매핑하여 저장한다.
- [ ] 등록된 전체 메뉴 정보를 조회할 수 있다.
  

### 메뉴 상품 
- [ ] 등록된 메뉴와 상품의 매핑 정보, 남은 수량을 등록할 수 있다.


### 주문
- [ ] 주문 테이블 id, 주문 상태, 주문한 시간, 주문 항목을 받아서 주문 정보를 등록할 수 있다.
  - [ ] 주문 정보와 주문한 상품의 정보를 매핑하여 저장한다.
  - [ ] 주문 항목이 입력되지 않으면 예외처리한다.
  - [ ] 주문한 메뉴 정보가 등록되어 있지 않으면 예외처리한다.
  - [ ] 주문한 테이블 정보가 등록되어 있지 않으면 예외처리한다.
  - [ ] 주문이 등록되면 주문 상태는 조리중인 상태로 바뀌고 주문한 시간이 현재 시간으로 저장된다.
- [ ] 등록된 전체 주문 정보를 조회할 수 있다.
- [ ] 등록된 주문의 주문 상태를 변경할 수 있다.
  - [ ] 등록된 주문의 주문 상태가 이미 완료처리된 상태라면 예외처리한다.


### 테이블 그룹
- [ ] 주문 테이블들의 정보를 받아서 테이블 그룹 정보를 등록할 수 있다.
  - [ ] 입력한 주문 테이블 정보가 없거나 하나인 경우 예외처리한다.
  - [ ] 등록되지 않은 주문 테이블 정보를 입력한 경우 예외처리한다.
  - [ ] 그룹을 지으려는 등록된 테이블 상태가 empty가 아니거나 이미 다른 그룹에 지정된 테이블인 경우 예외처리한다.
- [ ] 등록되어 있는 테이블 그룹 정보를 삭제할 수 있다.
  - [ ] 삭제하려는 테이블 그룹에 그룹핑되어있던 주문 테이블중에 주문 상태가 완료되지 않은 테이블들이 있다면 예외처리한다.


### 테이블
- [ ] 테이블에 방문한 손님 수, 테이블이 현재 empty 상태인지 여부 정보를 받아서 테이블 정보를 등록할 수 있다.
- [ ] 등록된 전체 테이블 정보를 조회할 수 있다.
- [ ] 등록된 주문 테이블 empty 상태를 변경할 수 있다.
  - [ ] 테이블 그룹에 속해있는 주문 테이블을 empty 상태로 변경하려는 경우 예외처리한다.
  - [ ] 아직 주문 상태가 완료되지 않은 테이블을 empty 상태로 변경하려는 경우 예외처리한다.
- [ ] 등록된 테이블에 방문한 손님 수를 변경할 수 있다.
  - [ ] 변경하려는 방문한 손님 수 입력이 음수이면 예외처리한다.
  - [ ] 방문한 손님 수를 입력한 테이블이 empty 상태이면 예외처리한다.



## 용어 사전

| 한글명 | 영문명 | 설명 |
| --- | --- | --- |
| 상품 | product | 메뉴를 관리하는 기준이 되는 데이터 |
| 메뉴 그룹 | menu group | 메뉴 묶음, 분류 |
| 메뉴 | menu | 메뉴 그룹에 속하는 실제 주문 가능 단위 |
| 메뉴 상품 | menu product | 메뉴에 속하는 수량이 있는 상품 |
| 금액 | amount | 가격 * 수량 |
| 주문 테이블 | order table | 매장에서 주문이 발생하는 영역 |
| 빈 테이블 | empty table | 주문을 등록할 수 없는 주문 테이블 |
| 주문 | order | 매장에서 발생하는 주문 |
| 주문 상태 | order status | 주문은 조리 ➜ 식사 ➜ 계산 완료 순서로 진행된다. |
| 방문한 손님 수 | number of guests | 필수 사항은 아니며 주문은 0명으로 등록할 수 있다. |
| 단체 지정 | table group | 통합 계산을 위해 개별 주문 테이블을 그룹화하는 기능 |
| 주문 항목 | order line item | 주문에 속하는 수량이 있는 메뉴 |
| 매장 식사 | eat in | 포장하지 않고 매장에서 식사하는 것 |
