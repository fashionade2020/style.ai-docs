# style.ai 상품

## 1. apikey
- style.ai 적용 사이트에 대한 apikey 별도 제공

## 2. SQS
- 상품 적용을 위한 SQS key, secret 별도 제공

## 3. 상품 명령어(type)
- 추가 : ADD
- 수정 : CHANGE
- 재고 변경 : CHANGE_STOCK

## 4. payload
### 4.1 상품 추가
- type : ADD
- apiKey : apikey
- name : 상품명
- productId : 쇼핑몰에서 관리하는 유니크 id (쇼핑몰에서 노출되는 것, ex : SM323UTS70)
- category2: 중 카테고리 (대 카테고리는 대시보드의 카테고리 매핑에 맞춰서 생성)
- desc : 상품 설명
- gender : NONE, MALE, FEMALE, UNISEX
- brand : 브랜드
- price : 판매 가격(Integer)
- originalPrice : 원가(Integer)
- imageUrl : 상품 이미지 주소
- removeBackground : true, false (상품이미지 배경제거 여부)
- origin : 원산지
- detailUrl : 상품 상세 페이지
- season : [SPRING, SUMMER, AUTUMN, WINTER]
- age : ADULT, JUNIOR, CHILD


#### 예제
```
{
  "type": "ADD",
  "apiKey": "asfdasdfsf234klj23kl4jldfu90fsdf",
  "item": {
    "name": "맨투맨",
    "productId": "a909203923",
    "category1": "남성",
    "category2": "상의",
    "category3": "맨투맨",
    "desc": "이쁜 맨투맨",
    "gender": "UNISEX", // NONE | MALE | FEMALE | UNISEX
    "brand": "GUESS",
    "price": 50000,
    "originalPrice": 70000,
    "imageUrl": "https://dfsf.com/1.jpg",
    "origin": "베트남",
    "detailUrl": "https://dfsf.com/a909203923",
    "stock": 10
  }
}

```
### 4.2 상품 수정
- type : CHANGE
- apiKey : apikey
- name : 상품명
- productId : 쇼핑몰에서 관리하는 유니크 id (쇼핑몰에서 노출되는 것, ex : SM323UTS70)
- category1: 대 카테고리
- category2: 중 카테고리
- category3: 소 카테고리
- desc : 상품 설명
- gender : NONE, MALE, FEMALE, UNISEX
- brand : 브랜드
- price : 판매 가격(Integer)
- originalPrice : 원가(Integer)
- origin : 원산지
- detailUrl : 상품 상세 페이지

#### 예제
```
{
  "type": "CHANGE",
  "apiKey": "asfdasdfsf234klj23kl4jldfu90fsdf",
  "item": {
    "name": "맨투맨",
    "productId": "a909203923",
    "category1": "남성",
    "category2": "상의",
    "category3": null,    
    "desc": "이쁜 맨투맨",
    "gender": "UNISEX",
    "brand": "GUESS",
    "price": 50000,
    "originalPrice": 70000,
    "origin": "베트남",
    "detailUrl": "https://dfsf.com/a909203923",
    "stock": 10
  }
}
```


