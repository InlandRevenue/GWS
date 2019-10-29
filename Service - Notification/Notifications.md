# Notifications
## Version: 

### /list

#### POST
##### Summary:

Notification service

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body |  | Yes | [list_POST_Request](#list_post_request) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | HttpStatus: 200 - OK | [list_POST_Response200](#list_post_response200) |
| 400 | HttpStatus: 400 - BadRequest | [list_POST_Response400](#list_post_response400) |
| 500 | HttpStatus: 500 - InternalServerError | [list_POST_Response500](#list_post_response500) |
| default |   | [list_POST_ResponseDefault](#list_post_responsedefault) |

### Models


#### list_POST_Request

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| QueryIDType | string | <p>The query ID type is the type of ID that is used to filter notifications</p><table><tbody><tr><th>code</th><th>description</th></tr><tr><td>CLTLID</td><td>Other Tax Preparer Client List Identifier</td></tr><tr><td>CST</td><td>A non-IRD Number type identifier. Given to customers who do not have an IRD number in the system</td></tr><tr><td>IRD</td><td>Inland Revenue Department ID</td></tr><tr><td>KSF</td><td>KiwiSaver Schemes ID</td></tr><tr><td>LSTID</td><td>Tax Agent List Identifier</td></tr></tbody></table> | No |
| QueryID | string | <p>The query ID is used to filter available notifications by recipient</p> | No |
| FromDateTime | dateTime | <p>The earliest point in time on which to select notifications based on their date-time stamp. This is an ISO8601 formatted datetime. Example: 2020-01-02T08:06:26</p> | Yes |
| ToDateTime | dateTime | <p>The latest point in time on which to select notifications based on their date-time stamp. This is an ISO8601 formatted date time. Example: 2020-01-15T15:53:00</p> | No |

#### list_POST_Response200

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| Notifications | [ object ] | <p>Notifications response array</p> | Yes |

#### list_POST_Response400

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| errors | [ object ] | Validation array | Yes |

#### list_POST_Response500

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| errors | [ object ] | Validation array | Yes |

#### list_POST_ResponseDefault

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| errors | [ object ] | Validation array | Yes |