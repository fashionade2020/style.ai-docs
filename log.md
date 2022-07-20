# 성과측정툴 개발자 가이드

### Common
curl -X POST https://logs.fashionade.ai/logs 로 요청을 보내는 형태이며 공통적으로 body 에 들어가는 데이터는 다음과 같습니다.

```
"type": "click", // 로그 타입 (init, click, addCart, purchase)
"apiKey": "XXXXXXX", // apiKey
"uuid": "/^[a-zA-Z0-9]+$/", // 랜덤 생성 unique id
"userAgent": "Mozilla", // user agent
"lang": "ko-Kr", // 브라우저 언어
"page": "https://www.sample.com/page.html" // 페이지 url
"referrer": "https://www.sample.com/refer" // 링크를 통해 현재 페이지로 이동 시킨, 전 페이지의 URI 정보
"deviceTime": "2020-09-09 12:00:00.000" // GMT+9
"ext": {
  "userId": "userId" // 유저아이디
}
```
### Page view 
추천 콘텐츠가 노출되는 모든 화면에서 수집하는 데이터입니다.

Page view 예시)

```
curl -X POST 'https://logs.fashionade.ai/logs' \
-d '{
  "sdk": "outfits",
  "type": "init",
  "apiKey": "qEPCePiBjV2Clk0rEwuSwEq6dddrici9YA2yRaTDa1s2d3f4q5w6e8r1h5b1b6b",
  "uuid": "user uuid",
  "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
  "lang":"ko-kr",
  "page":"https://www.fashionade.ai/item/64567",
  "referrer":"https://www.fashionade.ai/item/64568",
  "deviceTime":"2021-05-06T02:39:36.096Z",
  "ext": {
    "userId": "20211222test",
   },
}'
```



### 상품 클릭
추천 콘텐츠에서 상품을 클릭했을 때 수집하는 데이터 입니다.

상품 클릭 추가 데이터

```
"recommendItemId": "123123" // 추천 상품 Id 
```

상품 클릭 예시)

```
curl -X POST 'https://logs.fashionade.ai/logs' \
-d '{
  "sdk": "outfits",
  "type": "click",
  "apiKey": "qEPCePiBjV2Clk0rEwuSwEq6dddrici9YA2yRaTDa1s2d3f4q5w6e8r1h5b1b6b",
  "uuid": "user uuid",
  "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
  "lang":"ko-kr",
  "page":"https://www.fashionade.ai/item/64567",
  "referrer":"https://www.fashionade.ai/item/64568",
  "deviceTime":"2021-05-06T02:39:36.096Z",
  "ext": {
    "userId": "20211222test",
   },
   "recommendItemId": "123123"
}'
```

### 장바구니, 구매완료
장바구니와 구매완료 페이지는 type 을 제외한 데이터 양식이 같으며 items(json array)를 추가해주시면 됩니다.

```
items: [ 
  { 
    "orderId" : "20210926-0001", // 주문 Id 구매완료 시에만 사용
    "productId": "asdfzxcv12", // 상품 Id
    "currency": "KRW", // 공급가 통화 
    "price": 123, // 공급가 
    "saleCurrency": "KRW", // 판매가 통화 
    "salePrice": 123, // 판매가 
    "qty": 2, // 수량 
    "totalAmount": 246 // 수량 * 판매가
  }, ... 
]
```

장바구니 예시)

```
curl -X 'POST https://logs.fashionade.ai/logs' \
-d '{
  "sdk":"outfits",
  "type":"addCart",
  "apiKey":"qEPCePiBjV2Clk0rEwuSwEq6dddrici9YA2yRaTDa1s2d3f4q5w6e8r1h5b1b6b",
  "uuid":"a6dd3f32-5ce7-45c6-b818-2e8846a390a1",
  "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.69 Safari/537.36",
  "lang":"ko-KR",
  "page":"http://localhost:9000/",
  "referrer":"",
  "deviceTime":"2021-12-21T03:35:37.231Z",
  "ext":{
    "userId":"20211222test",
   },
   "eventPosition":0,
   "items":[
    {
      "productId":"asdfzxcv12",
      "currency":"KRW",
      "price":109000,
      "saleCurrency":"KRW",
      "salePrice":109000,
      "qty":2,
      "totalAmount":218000
    }
  ]
}'
```

구매완료 예시)

```
curl -X 'POST https://logs.fashionade.ai/logs' \
-d '{
  "sdk":"outfits",
  "type":"purchase",
  "apiKey":"qEPCePiBjV2Clk0rEwuSwEq6dddrici9YA2yRaTDa1s2d3f4q5w6e8r1h5b1b6b",
  "uuid":"a6dd3f32-5ce7-45c6-b818-2e8846a390a1",
  "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.69 Safari/537.36",
  "lang":"ko-KR",
  "page":"http://localhost:9000/",
  "referrer":"",
  "deviceTime":"2021-12-21T03:44:12.703Z",
  "ext":{
    "userId":"20211222test"
   },
   "items":[
    {
      "orderNo":"20210926-0001",
      "productId":"asdfzxcv12",
      "currency":"KRW",
      "price":109000,
      "saleCurrency":"KRW",
      "salePrice":109000,
      "qty":1,
      "totalAmount":109000
    }
  ]
}'
```

