# style.ai 유저, 주문

## 1. apikey
- style.ai 적용 사이트에 대한 apikey 별도 제공

## 2. SQS
- 상품 적용을 위한 SQS key, secret 별도 제공

## 3. 명령어(Type)
- 유저 : USER
- 주문상품 : ORDER_ITEM

## 4. payload
### 4.1 유저 추가
- type : USER
- apiKey : apikey
- userId : 유저아이디
- gender : 성별 (MALE, FEMALE, UNISEX)
- age : 연령
- email : 이메일
- mobile : 휴대폰 번호


#### 예제
```
{
  "type": "USER",
  "apiKey": "asfdasdfsf234klj23kl4jldfu90fsdf",
  "user": {
    "userId": "user1",
    "gender": "MALE",
    "age": "41",
    "email": "usermail@gmail.com",
    "mobile": "010-1234-5678",
  }
}


### 4.2 주문 상품 정보 연동
- type : ORDER_ITEM
- apiKey : apikey
- userId : 유저아이디
- productId: 상품의 아이디 혹은 일련번호


#### 예제
```
{
  "type": "ORDER_ITEM",
  "apiKey": "asfdasdfsf234klj23kl4jldfu90fsdf",
  "userId" : "user1",
  "productId" : "PHD0401"
}
