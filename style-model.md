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
    <td>http://15.165.230.228:3211/api/tryon</td>
    <td></td>
  </tr>
  <tr>
    <td>Request Body</td>
    <td>styleInfo</td>
    <td>하위참조</td>
  </tr>
</table>

## styleInfo
- tops : 상의
- bottoms : 하의 ( 하의의 경우에는 bottoms_sub_category 가 필수이며 "pants", "skirts" 중 택 1 )
- outerwear : 아우터

#### 예제
```
{
    "styleInfo": {
        "tops": {
            "gender": "female",
            "image_url" :"https://s3.ap-northeast-2.amazonaws.com/style.ai/devimages/164176935366889473/161936239803782208.png",
            "category" : "tops"
        },
        "outerwear": {
            "gender" : "female",
            "image_url" : "https://s3.ap-northeast-2.amazonaws.com/style.ai/devimages/164176935366889473/161936239856623808.png",
            "category" : "outerwear"
        },
        "bottoms": {
            "gender" : "female",
            "image_url" : "https://s3.ap-northeast-2.amazonaws.com/style.ai/devimages/164176935366889473/161869500333571547.png",
            "category" : "bottoms",
            "bottoms_sub_category": "pants"
        }
    }
}
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
    <td>모델이미지를 BASE64 포멧으로 제공 </td>
    <td></td>
  </tr>
</table>
