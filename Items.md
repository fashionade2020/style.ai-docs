# style.ai 상품

## 1. apikey
- style.ai 적용 사이트에 대한 apikey 별도 제공

## 2. SQS
- 상품 적용을 위한 SQS key, secret 별도 제공

## 3. 상품 명령어(type)
- 추가 : ADD
- 수정 : CHANGE

## 4. payload
### 4.1 상품 추가
- type : ADD
- apiKey : apikey
- removeBackground : true, false (상품이미지 배경제거 여부)
- name : 상품명
- productId : 쇼핑몰에서 관리하는 유니크 id (쇼핑몰에서 노출되는 것, ex : SM323UTS70)
- desc : 상품 설명
- price : 판매 가격(Integer)
- originalPrice : 원가(Integer)
- imageUrl : 상품 이미지 주소
- origin : 원산지
- detailUrl : 상품 상세 페이지
- stock: 재고
- sellingStatus : NOT_DISPLAY, SOLD_OUT, VALID (전시종료, 판매종료, 유효함)


#### 예제
```
{
  "type": "ADD",
  "apiKey": "asfdasdfsf234klj23kl4jldfu90fsdf",
  "removeBackground": "true",
  "item": {
    "name": "맨투맨",
    "productId": "a909203923",
    "desc": "이쁜 맨투맨",
    "price": 50000,
    "originalPrice": 70000,
    "imageUrl": "https://dfsf.com/1.jpg",
    "origin": "베트남",
    "detailUrl": "https://dfsf.com/a909203923",
    "stock": 10,
    "sellingStatus": "VALID"
  }
}

```
### 4.2 상품 수정
- type : CHANGE
- apiKey : apikey
- removeBackground : true, false (상품이미지 배경제거 여부)
- name : 상품명
- productId : 쇼핑몰에서 관리하는 유니크 id (쇼핑몰에서 노출되는 것, ex : SM323UTS70)
- desc : 상품 설명
- price : 판매 가격(Integer)
- originalPrice : 원가(Integer)
- imageUrl : 상품 이미지 주소
- origin : 원산지
- detailUrl : 상품 상세 페이지
- stock: 재고
- sellingStatus : NOT_DISPLAY, SOLD_OUT, VALID (전시종료, 판매종료, 유효함)

#### 예제
```
{
  "type": "CHANGE",
  "apiKey": "asfdasdfsf234klj23kl4jldfu90fsdf",
  "removeBackground": true,
  "item": {
    "name": "맨투맨",
    "productId": "a909203923",
    "desc": "이쁜 맨투맨",
    "price": 50000,
    "originalPrice": 70000,
    "imageUrl": "https://dfsf.com/1.jpg",
    "origin": "베트남",
    "detailUrl": "https://dfsf.com/a909203923",
    "stock": 10,
    "sellingStatus" : "VALID"
  }
}
```

## 5. 예시코드
### 5.1 AWS SDK for Java 1.x 

#### import
```
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.regions.Regions;
import com.amazonaws.services.sqs.AmazonSQS;
import com.amazonaws.services.sqs.AmazonSQSClientBuilder;
import com.amazonaws.services.sqs.model.SendMessageRequest;
```


#### 코드
```
AmazonSQS sqsClient = AmazonSQSClientBuilder.standard()
        .withRegion(Regions.fromName("ap-northeast-2"))
        .withCredentials(new AWSStaticCredentialsProvider(
                new BasicAWSCredentials("zxdtwqdgrtedfbbhqgsaw", "ojvoexalkcjeilsdmf")))
        .build();

String queueUrl = "https://sqs.ap-northeast-2.amazonaws.com/978986354907/item_test_20220408";
String messageBody = "{\n"
        + "  \"type\": \"ADD\",\n"
        + "  \"apiKey\": \"\",\n"
        + "  \"removeBackground\": false,\n"
        + "  \"item\": {\n"
        + "    \"name\": \"레더 벨트\",\n"
        + "    \"productId\": \"PRODUCTID_1\",\n"
        + "    \"price\": 10000,\n"
        + "    \"originalPrice\": 10000,\n"
        + "    \"imageUrl\": \"https://dfsf.com/1.jpg\",\n"
        + "    \"detailUrl\": \"https://dfsf.com/a909203923\",\n"
        + "    \"stock\": 5,\n"
        + "    \"sellingStatus\": \"VALID\"\n"
        + "  }"
        + "}";

SendMessageRequest sendMsgRequest = new SendMessageRequest()
        .withQueueUrl(queueUrl)
        .withMessageBody(messageBody)
        .withDelaySeconds(5);

sqsClient.sendMessage(sendMsgRequest);
```

