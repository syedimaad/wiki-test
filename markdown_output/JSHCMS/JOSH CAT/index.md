**Base URL:**
[**http://stage-cat.myjosh.in**](http://stage-cat.myjosh.in/login?path=https%3A%2F%2Fjot.myjosh.in%2Fcontent%2Fbrowse)**/**

#### 1. Login

Redirect to
<http://stage-cat.myjosh.in/login?path=https%3A%2F%2Fjot.myjosh.in%2Fcontent%2Fbrowse>

Send path query to redirect to after successful login.

Successful login will set the cookie and the set cookie will contain
ClientId, user UUID and user info in an encrypted form in Cookies.\
Cookie-name: `josh-cat-auth`. Also, The Client team will require to send
the redirect URL where they want to redirect the user after Login. Login
Page will be maintained by the CAS Team.

Cookie contains below information:

`jwt secret key : f359b338-8733-4ad4-8d31-5ae0488cfe41`

{ \"clientId\": \"test1@verse.in\", \"userUUID\":
\"4260416e-f7f9-49bb-be37-8e56544831bb\", \"userInfo\":
\"ee7UtJ/K9ujVlM77pSA5T824c6mt9B44XOW4ReZCrxDGGauwrbmF1GC4V9MPVsmVYkIPRXloE4IUhL7+sTBi9MkFonwVnzPza72aUaDgSVetO7Uy41VC+Mzy7JtxfnrYCgn22X0MbXiRAV+Onl07pkQbQqh/fbBeBageIHP8LAsa1Nnwj/8yW9xVbwsCtaUPucey9NEnSzfm0+5FqiV2javAqS0plfBNG8eYdWos9bkfh1e+ZX9h7HdqaGFlt1/509s/jSNXYYzMnpTHPJu0KJX5rh/mJAymTVgwa32WP6phiMJ2B59NrGz5AQ2BKLj8g+3CxS00WzkC5ZgL+/l+E+QDCQLt/GKfvIZMaMG2NNdPb3CF4nnfNgxxNGvoQIoQDy0V03lYX5vIs9tH9BN3/fxmtxdwDZVxU6UnfmXarV2FyQH30/VNRNZiU3s6c83ebDJdFh11vAMUo7yOgPP21Hew07PBoHafZVThfCJD2wSswpRtE6eNr6NAKyFM5+80TU/k74FPztqQ6tdM6HSu3wxuzC6cU9ldXpPG2OY1WxLScjDjreQ/bi1FXGiNDg=\",
\"iat\": 1652095750

} 

Get userInfo by Decryption

UserInfo Secret Key : `bbd07002-cf84-11ec-b804-bfe2a5b43ba8` +
`userUUID` (get from cookie)

#### 2. Forgot Password

Can do forget password from the login page itself.

**3. Change Password**

The Client Team will require to redirect to a new page with the
Destination URL in the path

Ex:
<http://stage-cat.myjosh.in>[/change-password?email=test1@verse.in&path=https%3A%2F%2Fjot.myjosh.in%2Fcontent%2Fbrowse](http://localhost:3000/change-password?email=test1@verse.in&path=https%3A%2F%2Fjot.myjosh.in%2Fcontent%2Fbrowse)

**Base URL:**
[**http://stage-cat.myjosh.in**](http://stage-cat.myjosh.in/login?path=https%3A%2F%2Fjot.myjosh.in%2Fcontent%2Fbrowse)**/**

**4. Get All Permissions**

GET `/auth/getAllPermissions`

cURL is given below

curl \--location \--request GET
\'http://stage-cat.myjosh.in/api/auth/getAllPermissions\'

**Response**

\[ { \"permissionId\": \"VIEW_MANAGE_CONTENT\", \"permissionStatus\":
\"active\", \"createdOn\": \"2022-04-27T12:54:23.172Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-27T12:54:23.172Z\" }, { \"permissionId\":
\"VIEW_BROWSE_CONTENT\", \"permissionStatus\": \"active\",
\"createdOn\": \"2022-04-27T12:54:17.494Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-27T12:54:17.494Z\" }, { \"permissionId\":
\"EDIT_BROWSE_CONTENT\", \"permissionStatus\": \"active\",
\"createdOn\": \"2022-04-27T12:54:10.230Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-27T12:54:10.230Z\" }, { \"permissionId\": \"EDIT_CONTENT\",
\"permissionStatus\": \"active\", \"createdOn\":
\"2022-04-26T12:12:42.454Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-26T12:12:42.454Z\" }, { \"permissionId\": \"VIEW_CONTENT\",
\"permissionStatus\": \"inactive\", \"createdOn\":
\"2022-04-26T12:08:08.614Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-26T12:08:08.614Z\" } \]

**5. Get Roles**

POST `/auth/getRoles`

**Case 1: cURL for the same if filter is applied on roleCode**

curl \--location \--request POST
\'http://localhost:3002/api/auth/getRoles\' \\ \--header \'Cookie:
JSESSIONID=AA9328B8C4EEC19D24A2CBCC4814EAF4\' \\ \--header
\'Content-Type: application/json\' \\ \--data-raw \' { \"roleCode\":
\"JOSHCMS_MANAGER\" }\'

**Request**

{ \"roleCode\": \"JOSHCMS_MANAGER\" }

**Response**

\[ { \"roleId\": 4, \"roleCode\": \"JOSHCMS_MANAGER\", \"roleName\":
\"MANAGER\", \"roleStatus\": \"active\", \"appCode\": \"3\",
\"permissions\": \[ \"EDIT_BROWSE_CONTENT\", \"VIEW_BROWSE_CONTENT\",
\"VIEW_MANAGE_CONTENT\", \"EDIT_MANAGE_CONTENT\" \], \"createdOn\":
\"2022-04-25T14:12:15.045Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-25T14:12:15.045Z\" } \]

**Case 1: cURL for the same if filter not applied**

curl \--location \--request POST
\'http://localhost:3002/api/auth/getRoles\' \\ \--header \'Cookie:
JSESSIONID=AA9328B8C4EEC19D24A2CBCC4814EAF4\' \\ \--data-raw \'\'

**Response**

\[ { \"roleId\": 4, \"roleCode\": \"JOSHCMS_MANAGER\", \"roleName\":
\"MANAGER\", \"roleStatus\": \"active\", \"appCode\": \"3\",
\"permissions\": \[ \"EDIT_BROWSE_CONTENT\", \"VIEW_BROWSE_CONTENT\",
\"VIEW_MANAGE_CONTENT\", \"EDIT_MANAGE_CONTENT\" \], \"createdOn\":
\"2022-04-25T14:12:15.045Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-25T14:12:15.045Z\" }, { \"roleId\": 3, \"roleCode\":
\"JOSHCMS_ADMIN\", \"roleName\": \"ADMIN\", \"roleStatus\": \"active\",
\"appCode\": \"1\", \"permissions\": \[ \"EDIT_BROWSE_CONTENT\",
\"VIEW_BROWSE_CONTENT\", \"VIEW_MANAGE_CONTENT\", \"EDIT_CONTENT\" \],
\"createdOn\": \"2022-04-25T11:59:32.393Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-25T11:59:32.393Z\" }, { \"roleId\": 2, \"roleCode\":
\"JOSHCMS_PROMOTION\", \"roleName\": \"ADMIN\", \"roleStatus\":
\"active\", \"appCode\": \"1\", \"permissions\": \[
\"EDIT_BROWSE_CONTENT\", \"VIEW_BROWSE_CONTENT\" \], \"createdOn\":
\"2022-04-25T11:05:47.330Z\", \"createdBy\":
\"nishant.pratap@verse.in\", \"modifiedOn\":
\"2022-04-25T11:05:47.330Z\" } \]

**7. Logout**

GET `/auth/logout`

cURL is given below

curl \--location \--request GET
\'http://stage-cat.myjosh.in/api/auth/logout\'

**Response**

{ \"message\": \"Logout Successfully.\" }

**8. Get userList by Applicatiom**\
POST `/user/getUsersByApplication`

cURL is given below

curl \--location \--request POST
\'http://stage-cat.myjosh.in/api/user/getUsersByApplication\' \\
\--header \'Cookie:
josh-cat-auth=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjbGllbnRJZCI6InRlc3QyQHZlcnNlLmluIiwidXNlclVVSUQiOiIyYWM2MWM3Mi1iOGZhLTQ1ZmEtYWU4Mi0yNmViNzQxNWViYjciLCJ1c2VySW5mbyI6IlUyRnNkR1ZrWDEvazZTak9lWkRHYjV2TmxvRmZSZ0dFQncrTUM2NTlvSEwxK1RxV1FScDFIZXVEL1MraHZCdjVNVEc3dzlZV1ZSMXZRVWhpY3YvSWI4R21RSGg5Mmo0TUlqVmEzejZlbVQycis3bi9qT3A0a0FMMzIxQlp1azJrVlFtS0dxTThndWlUUlp0S2ZUL0x3UGJsN0tsTFdTVUIvVmpqckVTMkVpK08vZGRZMVE5bEVMWis0S1VwSzZlZnpteUxtRTRzWE5tZHZwN1VGdWhrUmd0S0tlYWxFRFpjK3l4cFRxeVZhUFI5eFgyc0VTRUtNZTZZUEs0UG1Ucyt6cVBwK1ZVUVFvM0l5alRUZ2VNMFVEaVRyOXExcmpyaVI4ZGcxTExuQXhiVGdQbit4cjU5QzNKSS9IR215RUg5R2xyRHVmbEd0RStxUFFFam1CWTh5aWQ4R0pNU2F4bVZJM2VtSTZNLzhRZjJUajJubzVBQ1dIL2lrNTVmY1EzblpKaWpsWWViS0dic1FzY1o4Rmtsd0lDaHpTOXduQTl3b0ttOU1XaE9CWFRTbmdNdTZkQWpXNFZhUVN1dzR1cEF1Vlo5MmpVaUdTRUdPU2R2R2YxaHpwREVNRUJpeDZUQWMvOWtSc3E3US8xR1RXbXJ5RUh2cDd0SitjWkx3eWM5NXYyLytHUE1PaHhUdHo2MUhUM0kvUnNoZGhQRk9VbDhKRkNVZVUyS2M0VWM2Y3hRMUtWMnBPRXkzdG5VRGdYbHczSmttTG9UZFUyQWkyWnNiVHdaOXgzSm5McjVwNXIyd3lhM3o3Yzlvd3c9IiwiaWF0IjoxNjUyODU0ODc5fQ.IegmyLw7CbxUoJwni90Gh7jpen4pqPYmNo1YDJ5FSv;
josh-cat-auth=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjbGllbnRJZCI6InRlc3QyQHZlcnNlLmluIiwidXNlclVVSUQiOiIyYWM2MWM3Mi1iOGZhLTQ1ZmEtYWU4Mi0yNmViNzQxNWViYjciLCJ1c2VySW5mbyI6IlUyRnNkR1ZrWDEvazZTak9lWkRHYjV2TmxvRmZSZ0dFQncrTUM2NTlvSEwxK1RxV1FScDFIZXVEL1MraHZCdjVNVEc3dzlZV1ZSMXZRVWhpY3YvSWI4R21RSGg5Mmo0TUlqVmEzejZlbVQycis3bi9qT3A0a0FMMzIxQlp1azJrVlFtS0dxTThndWlUUlp0S2ZUL0x3UGJsN0tsTFdTVUIvVmpqckVTMkVpK08vZGRZMVE5bEVMWis0S1VwSzZlZnpteUxtRTRzWE5tZHZwN1VGdWhrUmd0S0tlYWxFRFpjK3l4cFRxeVZhUFI5eFgyc0VTRUtNZTZZUEs0UG1Ucyt6cVBwK1ZVUVFvM0l5alRUZ2VNMFVEaVRyOXExcmpyaVI4ZGcxTExuQXhiVGdQbit4cjU5QzNKSS9IR215RUg5R2xyRHVmbEd0RStxUFFFam1CWTh5aWQ4R0pNU2F4bVZJM2VtSTZNLzhRZjJUajJubzVBQ1dIL2lrNTVmY1EzblpKaWpsWWViS0dic1FzY1o4Rmtsd0lDaHpTOXduQTl3b0ttOU1XaE9CWFRTbmdNdTZkQWpXNFZhUVN1dzR1cEF1Vlo5MmpVaUdTRUdPU2R2R2YxaHpwREVNRUJpeDZUQWMvOWtSc3E3US8xR1RXbXJ5RUh2cDd0SitjWkx3eWM5NXYyLytHUE1PaHhUdHo2MUhUM0kvUnNoZGhQRk9VbDhKRkNVZVUyS2M0VWM2Y3hRMUtWMnBPRXkzdG5VRGdYbHczSmttTG9UZFUyQWkyWnNiVHdaOXgzSm5McjVwNXIyd3lhM3o3Yzlvd3c9IiwiaWF0IjoxNjUyODU0ODc5fQ.IegmyLw7CbxUoJwni90Gh7jpen4pqPYmNo1YDJ5FSvs\'
\\ \--header \'Content-Type: application/json\' \\ \--data-raw \'{
\"appCode\" : \"CREATOR_NETWORK\" }\'

**Request**

{ \"appCode\" : \"CREATOR_NETWORK\" }

**Response**

\[ { \"name\": \"Akshay Gupta\", \"email\":
\"akshay.gupta@techugo.com\", \"roles\": \[
\"CREATOR_NETWORK_AUDIO_MANAGER\" \], \"userUUID\":
\"7d1ec14a-de89-4d54-b348-6b34dd071f60\" }, { \"name\": \"Ambika
Verma\", \"email\": \"ambika.verma@techugo.com\", \"roles\": \[
\"CREATOR_NETWORK_AUDIO_MANAGER\" \], \"userUUID\":
\"44ea4969-fe23-4370-ae5e-e898ad1ed255\" }, { \"name\": \"Ayush
Pandey\", \"email\": \"ayush.pandey@techugo.com\", \"roles\": \[
\"CREATOR_NETWORK_ADMIN\" \], \"userUUID\":
\"94812b06-d219-481c-8fbe-6f73054d360a\" }, { \"name\": \"Deepak
Kumar\", \"email\": \"deepak.kumar@techugo.com\", \"roles\": \[
\"CREATOR_NETWORK_ADMIN\" \], \"userUUID\":
\"5c5e4a7d-159c-4448-907a-3a35e305626b\" }, { \"name\": \"Jay Kapasi\",
\"email\": \"jay.kapasi@verse.in\", \"roles\": \[
\"CREATOR_NETWORK_AUDIO_MANAGER\", \"CREATOR_NETWORK_ADMIN\" \],
\"userUUID\": \"e8750ce5-da34-42bc-97a6-22f3bc02cb75\" }, { \"name\":
\"Karandeep Gujral\", \"email\": \"karandeep.gujral@verse.in\",
\"roles\": \[ \"CREATOR_NETWORK_AUDIO_MANAGER\",
\"CREATOR_NETWORK_ADMIN\" \], \"userUUID\":
\"cf59b0ff-4ff3-4ff2-b5b6-89ced45752d2\" }, { \"name\": \"Shahnazar\",
\"email\": \"shahnazar@techugo.com\", \"roles\": \[
\"CREATOR_NETWORK_ADMIN\", \"CREATOR_NETWORK_AUDIO_MANAGER\" \],
\"userUUID\": \"dba03064-7f31-4c8f-8fc0-1e5d3144d44d\" }, { \"name\":
\"Veerendra\", \"email\": \"veerendra@techugo.com\", \"roles\": \[
\"CREATOR_NETWORK_ADMIN\", \"CREATOR_NETWORK_AUDIO_MANAGER\" \],
\"userUUID\": \"8ea7183c-4bfd-4dc4-af08-bb9c78ae9287\" } \]
