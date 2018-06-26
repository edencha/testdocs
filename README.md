# testdocs
test
# 그룹 목록

메시지 그룹 목록 조회 API 사용방법을 기술합니다.

이전에 삭제 되었거나, 생성 실패된 메시지 그룹을 포함한 모든 그룹 조회가 가능합니다.

## Request

{% tabs %}
{% tab title="URI" %}
{% api-method method="get" host="https://rest.coolsms.co.kr" path="/messages/v4/groups" %} {% api-method-summary %} 메시지 그룹 목록 조회 {% endapi-method-summary %}
{% endtab %}

{% tab title="Sample" %}
`url -X GET https://rest.coolsms.co.kr/messages/v4/groups  --header "Authorization : HMAC-SHA256 ApiKey=[API_KEY], Date=[DATE], Salt=[UNIQID], Signature= [SIGNATURE]"`
{% endtab %}
{% endtabs %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
인증정보
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %} {% api-method-parameter name="offset" type="number" required=false %} 검색 시작 기준점
(default: 0) {% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %} 1회 요청 시 조회할 최대 데이터 수
(default: 20, max: 500) {% endapi-method-parameter %}

{% api-method-parameter name="criteria" type="string" required=false %} 그룹 검색 기준 ,(콤마)로 구분하여 여러 검색 기준을 사용
* `groupId` - 그룹 아이디
* `status` - 그룹 상태
* `dateCreated` - 그룹 생성일
* `dateUpdated` - 그룹 수정일
* `scheduledDate` - 그룹 예약 발송일
{% endapi-method-parameter %}

{% api-method-parameter name="cond" type="string" required=false %} 검색 시 사용되는 비교 연산자
* `eq` - 검색 값과 같은 데이터
* `ne` - 검색 값과 같지 않은 데이터
* `gte` - 검색 값보다 크거나 같은 데이터
* `gt` - 검색 값보다 큰 데이터
* `lte` - 검색 값보다 작거나 같은 데이터
* `lt` - 검색 값보다 작은 데이터
{% endapi-method-parameter %}

{% api-method-parameter name="value" type="string" %} 검색 값 {% endapi-method-parameter 
{% endapi-method-request %}

## Response

{% tabs %}
{% tab title="Syntax" %}
```text
{
    "offset": Number, 
    "limit": Number, 
    "totalCount": Number, 
    "groupList": { 
        "String": { 
            "agent": { 
                "appId": "String", 
                "appVersion": "String", 
                "sdkVersion": "String", 
                "osPlatform": "String" 
            }, 
            "count": { 
                "sms": Number, 
                "lms": Number, 
                "mms": Number, 
                "ata": Number, 
                "cta": Number, 
                "push": Number 
            }, 
            "log": Array, 
            "groupId": "String", 
            "status": "String", 
            "accountId": "String", 
            "apiVersion": "String", 
            "_id": "String"
        } 
    }
}
```
{% endtab %}

{% tab title="Sample" %}
```text
{ 
    "offset": 0, 
    "limit": 20, 
    "totalCount": 1, 
    "groupList": { 
        "G4V20180307105937H3PTASXMNJG2JID": { 
            "agent": { 
                "appId": "MYAPPID", 
                "appVersion": null, 
                "sdkVersion": null, 
                "osPlatform": null 
            }, 
            "count": { 
                "sms": 0, 
                "lms": 0, 
                "mms": 0, 
                "ata": 0, 
                "cta": 0 
            }, 
            "log": [ 
                { 
                    "date": "2018-04-03 15:32:21", 
                    "message": "메시지 그룹 생성", 
                    "agent": { 
                        "appId": "MYAPPID", 
                        "appVersion": null, 
                        "sdkVersion": null, 
                        "osPlatform": null 
                    }
                } 
            ], 
            "groupId": "G4V20180307105937H3PTASXMNJG2JID", 
            "status": "PENDING", 
            "accountId": "12925149", 
            "apiVersion": "4", 
            "_id": "G4V20180307105937H3PTASXMNJG2JID" 
        } 
    } 
}
```
{% endtab %}
{% endtabs %}

* `offset` - 그룹 목록 조회 시작점
* `limit` - 최대 조회 그룹 수
* `totalCount` - 등록 된 총 그룹 수
* `groupList` - 그룹 목록
  * `groupId` - 그룹 고유 값
    * `agent` - 사용자 agent 정보
      * `appId` - 그룹 생성 시 함께 요청한 appId
      * `appVersion` - 그룹 생성 시 함께 요청한 앱 버전
      * `sdkVersion` - sdk를 이용하여 발송한 경우 해당 sdk의 버전
      * `osPlatform` - 그룹 생성 시 함께 요청한 운영체제 환경
    * `count` - 그룹에 등록되어 있는 문자메시지 수
      * `sms` - 그룹에 등록된 sms 수
      * `lms` - 그룹에 등록된 lms 수
      * `mms` - 그룹에 등록된 mms 수
      * `ata` - 그룹에 등록된 ata 수
      * `cta` - 그룹에 등록된 cta 수
    * `log` - 해당 메시지 그룹의 모든 이력 정보
    * `groupId` - 해당 메시지 그룹의 아이디
    * `status` - 해당 메시지 그룹의 상태 정보. \(자세한 사항은 그룹정보조회 문서 참조\)
    * `accountId` - 사용자 고유 값
    * `apiVersion` - 요청에 사용된 api 버전 정보
    * `_id` - groupId와 동일한 그룹 고유 값

