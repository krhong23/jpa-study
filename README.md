# jpa-study
JPA 프로그래밍 예제 실습

## 1. 요구사항 분석과 기본 매핑

### 요구사항 분석
- 핵심 요구사항
    - 회원은 상품을 주문할 수 있다.
    - 주문 시 여러 종류의 상품을 선택할 수 있다.

### 도메인 모델 분석
- 엔티티 도출
    - 회원
    - 주문
    - 상품
    - 주문상품 

- 회원과 주문의 관계: 회원은 여러 번 주문할 수 있음 -> 회원과 주문은 일대다 관계(1:N)
- 주문과 상품의 관계: 주문할 때 여러 상품을 함께 선택할 수 있음, 같은 상품도 여러 번 주문될 수 있음 -> 주문 상품(연결 엔티티) 추가해서 다대일 관계(N:1)

### 테이블 설계
- 회원(MEMBER): 이름(name)과 주소 정보(city, street, zipcode)
- 주문(ORDERS): 주문한 회원(member_id, FK), 주문 날짜(orderdate), 주문 상태(status)
- 주문상품(ORDER_ITEM): 주문(order_id, FK), 주문한 상품(item_id, FK), 주문 금액(orderprice), 주문 수량(count)
- 상품(ITEM): 이름(name), 가격(price), 재고수량(stockquantity)

### 엔티티 설계와 매핑
+ UML

### 데이터 중심 설계의 문제점
지금 방식은 객체를 테이블 설계에 맞춘 방법이다.

객체는 참조를 사용해서 연관된 객체를 찾고 테이블은 외래 키를 사용해서 연관된 테이블을 찾으므로 둘 사이에는 큰 차이가 있다.

JPA는 객체의 참조와 테이블의 외래 키를 매핑해서 객체에서는 참조를 사용하고 테이블에서는 외래 키를 사용할 수 있도록 한다.