# Virtual Try on API 


### Request Format
<table>
  <tr>
    <th>항목</th>
    <th>설명</th>
  </tr>
  <tr>
    <td>Method</td>
    <td>POST</td>
  </tr>
  <tr>
    <td>API Endpoint</td>
    <td>https://styleapi.fashionade.ai/api/vton</td>
  </tr>
  <tr>
    <td>Request Body</td>
    <td>하위참조</td>
  </tr>
</table>

## Parameter
<table>
  <tr>
    <th>Parameter</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>modelId</td>
    <td>
      모델 Id <br/>
      필수값으로 Style.AI에 등록된 모델의 Id
    </td>
  </tr>
  <tr>
    <td>TopId</td>
    <td>
      상의 상품 ID <br/>
      원피스 상품 ID 가 없는 경우, 상의 & 하의 상품 ID는 반드시 있어야함  <br/>
      원피스 상품 ID 가 있는 경우, 상의 & 하의 상품 ID는 없어야 함
    </td>
  </tr>
  <tr>
    <td>BottomId</td>
    <td>
      하의 상품 ID <br/>
      원피스 상품 ID 가 없는 경우, 상의 & 하의 상품 ID는 반드시 있어야함 <br/>
      원피스 상품 ID 가 있는 경우, 상의 & 하의 상품 ID는 없어야 함
    </td>
  </tr>
    <tr>
    <td>OuterId</td>
    <td>
      아우터 상품 ID <br/>
      필수값이 아님
    </td>
  </tr>
    <tr>
    <td>OnePieceId</td>
    <td>
      원피스 상품 ID <br/>
      원피스 상품 ID 가 없는 경우, 상의 & 하의 상품 ID는 반드시 있어야함 <br/>
      원피스 상품 ID 가 있는 경우, 상의 & 하의 상품 ID는 없어야 함
    </td>
  </tr>
    <tr>
    <td>ShoesId</td>
    <td>
      신발 상품 ID <br/>
      필수값이 아님
    </td>
  </tr>
    <tr>
    <td>EtcId</td>
    <td>
      기타 상품 ID <br/>
      필수값이 
    </td>
  </tr>
</table>

#### 예제
```
curl -X POST 'https://styleapi.fashionade.ai/api/vton' -H 'Content-Type: application/json' -d '{
      "modelId": "",
      "topId": "",
      "bottomId": "",
      "outerId": "",
      "onePieceId": "",
      "shoesId": "",
      "etcId": ""      
}'
```


### Response Format
<table>
  <tr>
    <th>항목</th>
    <th>설명</th>
    <th>세부내용</th>
  </tr>
  <tr>
    <td>Status</td>
    <td>API 요청 성공여부</td>
    <td>Success or failure</td>
  </tr>
  <tr>
    <td>Message</td>
    <td>Status가 Failure인 경우 상세 에러 메세지</td>
    <td>ex) Invalid image url, please ensure the file is of correct size and format</td>
  </tr>
  <tr>
    <td>Data</td>
    <td>모델이미지를 URL 포멧으로 제공 </td>
    <td></td>
  </tr>
</table>
