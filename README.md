# 使用 wiremock mock api
參考:
http://wiremock.org/docs/running-standalone/

下載本專案: git clone https://github.com/timmyBeef/mock-api.git

下面有兩個資料夾 mappings 和 __files 和一個 wiremock-standalone-2.24.1.jar

## mappings 和 __files

mappings: 放 api 的定義 json 檔案
__files: 放回傳的資料 json 檔案

例子:
mappings 下有個 policy-query.json, 內容是 api 的 request 和 response 的描述, 其中 response 用到 policy-query-response.json (回傳的資料)

policy-query-response.json 這個檔案就會放在 __files 下面

**policy-query.json** (api 的 request 和 response 的描述)
```
{
    "request": {
        "method": "POST",
        "url": "/api/e-commerce/policy/query"
    },
    "response": {
        "status": 200,
        "headers": {
            "Content-Type": "application/json"
        },
        "bodyFileName": "policy-query-response.json"
    }
}
```
**policy-query-response.json** (policy-query.json 裡面指定的回傳的資料)
```
{
  "policies": [
    {
      "quotationCode": "20001002436525",
      "policyCode": "TEST80021821",
      "mainProductCode": "TA",
      "mainCoverageName": "TA",
      "inceptionDatetime": "2017-05-02T12:00:00",
      "issueDatetime": "2017-02-09T10:41:08",
      "policyStatus": "ISSUED_WITH_PERM",
      "proposerName": "王大明_T",
      "insuredName": "王大明_T",
      "policyPrem": 29,
      "accountings": []
    },
    ...略
```



## 執行方式
```shell=
java -jar wiremock-standalone-2.24.1.jar --port 指定的 port 數字
```
不指定 port 預設就是 8080


![](https://i.imgur.com/yCTFvgW.png)

## 打 api 成功!
![](https://i.imgur.com/39jCKai.png)
