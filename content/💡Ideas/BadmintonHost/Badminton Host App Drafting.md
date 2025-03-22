---
date: 2025-03-21T09:44:50+07:00
---
- Ứng dụng hỗ trợ quản lý bài đăng cho host sân cầu lông
-
    - **Unworkable**: Causes major inefficiencies or job loss (e.g., iPhone activation failures).
    - **Unavoidable**: A necessary expense/problem (e.g., taxes, aging, education).
    - **Urgent**: A priority problem requiring immediate action (e.g., COVID-19, financial security).
    - **Underserved**: A market with high demand but no viable solution (e.g., affordable robotics toys in Africa).

[[How to Build a Product that Scales into a Company#**Summary of "How to Build a Product that Scales into a Company"**]]

Vấn đề của tuyển vãng lai + cố định trên các diễn đàn, group cầu lông:
1. Cấu trúc đầy đủ của 1 bài post tuyển vãng lai, cố định là gì?
	1. Vãng lai / Cố định? Both?
	2. Thời gian: ngày, giờ (0-24h), thời lượng chơi
	3. Sân (Tên + Địa chỉ + google map, hình ảnh của sân,...) - số thứ tự sân
	4. Trình độ (framework: Yếu - TB - Tốt) - Giới tính + Số lượng
	5. Cầu sử dụng
	6. Phí (cọc slot hoặc không) nam/nữ giá khác nhau
	7. Có/Không độ kèo, chai nước, bla bla 
	8. Tiện ích khác: trà đá, gửi xe,
	9. Số lượng người/sân
	10. Liên lạc, link Nhóm nếu có
	11. Hình ảnh/video trình độ
2. Điều gì ở những bài post tuyển vãng lai cần được cải thiện để có đủ thông tin hơn?
3. Vấn đề ở những bài đăng hiện tại là gì?
4. Ngữ cảnh ở đây là gì? Một nơi để mọi trình độ cầu lông được gặp gỡ nhau
5.  Ai là người sử dụng ứng dụng này? Cả hai dạng người này đều mong muốn gặp được những người mới + đường cầu lạ. 
	1. Chủ sân (Host)
		1. Bài viết nên kèm video (của mình hoặc những video ngang trình với nhóm mình
	2. Vãng lai
		1. Muốn được biết level hiện tại của bản thân
		2. Muốn biết review hạ tầng, sân bãi ntn, đèn chói, bla bla...
		3. Vị trí các sân, nhóm gần mình theo thời gian thực để kiếm slot vãng lai (nhóm chat dễ trôi quá)

Ứng dụng này offer cái gì, giải quyết vấn đề gì:
1. Biết rõ về trình độ hiện tại của end-user
2. Biết rõ về trình độ hiện tại của nhóm (host)

|     | Host                                                                           | Vãng lai |
| --- | ------------------------------------------------------------------------------ | -------- |
| 1   | Đôi lúc hay nhầm lẫn về số lượng tuyển                                         |          |
| 2   | Quên mất contact của những người trưởng tại vì dùng Messenger/Zalo để nickname |          |
| 3   | Đôi lúc quên đăng bài tuyển vãng lai                                           |          |
| 4   |                                                                                |          |

---


> [!IMPORTANT] Important
> - No login required | but will use **phone number to verify post register + create post**
> - No typing, choose templates instead
> - Free
> - Using phone number as contact only
> - Integrate well with Facebook
> - Using AI to simplify + improve the accuracy of the matching

Tính năng của MVP:
- **Must have**
	- Post to find member/team between (using templates and pre-defined rule, with additional information)
	- **get the current time, place to already filter the posts**
	- (In order to know the level of the user) see some references about the levels ??? How to define levels of users
	- Save as image to post into Facebook

**Post Table**

| id  | time      | date_of_week | level      | fee_male | fee_female | shuttle      | field    | court_no | author   | attachments | original_post_url | add_information | warning |
| --- | --------- | ------------ | ---------- | -------- | ---------- | ------------ | -------- | -------- | -------- | ----------- | ----------------- | --------------- | ------- |
|     | [from;to] | [0,6]        | [level_id] | int      | int        | [shuttle_id] | field_id | int      | json_str | [urls]      | url               | string          | url     |

**Shuttle Table**

| id  | name   | material                          | speed                       | durability   |
| --- | ------ | --------------------------------- | --------------------------- | ------------ |
|     | string | (enum) Feather - Plastic - Hybrid | (enum) Slow - Medium - Fast | (int) [1;10] |

**Level Table**

| id  | name | skill_required | description |
| --- | ---- | -------------- | ----------- |
|     |      |                |             |


Badminton Field Table (TBD)

| id  | name | location | court_type              | surface_type                     | no_of_court | lat | long | urls     |
| --- | ---- | -------- | ----------------------- | -------------------------------- | ----------- | --- | ---- | -------- |
|     |      |          | (enum) Indoor - Outdoor | (enum) Wood - Synthetic - Cement | (int) > 0   |     |      | [string] |



![[BadmintonHostMockup.svg|491]]

```curl
curl --location 'http://localhost:11434/api/chat' \
--header 'Content-Type: application/json' \
--data '{
    "model": "gemma2:2b",
    "messages": [
        {
            "role": "user",
            "content": "Lets extract data form the following post with precision, the post is about the recuitment for a badminton section. time is the duration in 12-hour format or 24-hour format, date_of_week is from Monday to Sunday, player_level is the skills required, fee_male is th price if recruiter is male, fee_female is the price of recruiter is female have to pay, shuttle_name is the name of the shuttlecock used,court_no is the number of court, address_information is the location"
        },
        {
            "role": "user",
            "content": "extract this post \n```\nMình tìm Vãng lai Nhà Tập luyện Phú Thọ (219 Lý Thường Kiệt, P15, Q11)\n🏸🏸🏸 T4 (19/03) 🏸🏸🏸\n🍻 14g - 16g\n🍻 15g - 17g\n🍻 19g - 21g\n Trình: tb-, tb\n🧏🏽‍♂️ Nam 60k | 🧏🏼‍♀️ Nữ 50k (sau 17g +5k)\nLH: 0787662388\n```\ndata"
        }
    ],
    "stream": false,
    "format": {
        "type": "object",
        "properties": {
            "address_information": {
                "type": "string"
            },
            "time": {
                "type": "string"
            },
            "date_of_week": {
                "type": "string"
            },
            "player_level": {
                "type": "string"
            },
            "fee_male": {
                "type": "string"
            },
            "fee_female": {
                "type": "string"
            },
            "shuttle_name": {
                "type": "string"
            },
            "field_name": {
                "type": "string"
            },
            "court_no": {
                "type": "string"
            },
            "author": {
                "type": "string"
            },
            "attachments": {
                "type": "string"
            },
            "original_post_url": {
                "type": "string"
            },
            "warning": {
                "type": "string"
            }
        },
        "required": [
            "address_information",
            "time",
            "date_of_week",
            "player_level",
            "fee_male",
            "fee_female",
            "shuttle_name",
            "field_name"

        ]
    },
    "options": {
        "temperature": 0
    }
}'
```