# Style Model API 


### Request Format
<table>
  <tr>
    <th>항목</th>
    <th>설명</th>
    <th>세부내용</th>
  </tr>
  <tr>
    <td>Method</td>
    <td>POST</td>
    <td></td>
  </tr>
  <tr>
    <td>API Endpoint</td>
    <td>http://15.165.230.228:3211/api/styleai/tryon</td>
    <td></td>
  </tr>
  <tr>
    <td>Request Body</td>
    <td>styleInfo</td>
    <td></td>
  </tr>
</table>





```
"type": "click", // 로그 타입 (click, addCart, purchase)
"apiKey": "XXXXXXX", // 이전에 전달드린 데상트 apiKey
"uuid": "/^[a-zA-Z0-9]+$/", // 랜덤 생성 unique id
"userAgent": "Mozilla", // user agent
"lang": "ko-Kr", // 브라우저 언어
"page": "https://www.sample.com/page.html", 페이지 url"referrer": "https://www.sample.com/refer", 링크를 통해 현재 페이지로 이동 시킨, 전 페이지의 URI 정보
"deviceTime": "2020-09-09 12:00:00.000" // GMT+9
"ext": {
  "userId": "userId" // 유저아이디
}
```


### Response Format
|항목|설명|세부내용|
|------|---|---|
|Status|API 요청 성공여부||
|Message|||
|Data|styleInfo||
