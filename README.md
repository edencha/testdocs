# README

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







{% api-method method="get" host="https://api.cakes.com" path="/v1/cakes/:id" %}
{% api-method-summary %}
Get Cakes
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" %}
ID of the cake to get, for free of course.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
Authentication token to track down who is emptying our stocks.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="recipe" type="string" %}
The API will do its best to find a cake matching the provided recipe.
{% endapi-method-parameter %}

{% api-method-parameter name="gluten" type="boolean" %}
Whether the cake should be gluten-free or not.
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



