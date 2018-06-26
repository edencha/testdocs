# README

그룹 검색 기준 ,\(콤마\)로 구분하여 여러 검색 기준을 사용

* `groupId` - 그룹 아이디
* `status` - 그룹 상태
* `dateCreated` - 그룹 생성일
* `dateUpdated` - 그룹 수정일
* `scheduledDate` - 그룹 예약 발송일

검색 시 사용되는 비교 연산자

* `eq` - 검색 값과 같은 데이터
* `ne` - 검색 값과 같지 않은 데이터
* `gte` - 검색 값보다 크거나 같은 데이터
* `gt` - 검색 값보다 큰 데이터
* `lte` - 검색 값보다 작거나 같은 데이터
* `lt` - 검색 값보다 작은 데이터

검색 값 {% endapi-method-parameter

{% api-method method="get" host="https://api.cakes.com" path="/v1/cakes/:id" %}
{% api-method-summary %}
Get Cakes
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="t" type="string" required=false %}
test
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "name": "Cake's name",
    "recipe": "Cake's recipe name",
    "cake": "Binary cake"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```javascript
{
    "message": "Ain't no cake like that."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



