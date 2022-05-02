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
    <td rowspan="3">Request Body</td>
    <td>styleInfo</td>
    <td></td>
  </tr>
</table>


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
|항목|설명|세부내용|
|------|---|---|
|Status|API 요청 성공여부||
|Message|||
|Data|styleInfo||
