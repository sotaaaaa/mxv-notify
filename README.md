## 1. Quản lý message
### 1.1 Publish message đến service notify

Channel: ```PUSH_NOTIFY```

Message: (Lưu ý: Message phải được gửi dưới dạng `stringify`)
```js
{
    "receivers": ["60e2892ddf72ff0939c61c35"],
    "data": {
        "message": "Day la thong bao",
        "type": "POST_CREATED",
        "icon": "post_created"
        "customJson": {
            "username": "Dung",
            "post_id": "12362173621cdsbdh"
        }
    },
    "type": "FORUM"
}
```

### A. Các trường bắt buộc:

```receivers```: Danh sách các user nhận thông báo này (gửi dưới dạng `ObjectId`)

```type```: Thuộc các loại thông báo dưới đây
- `FORUM`: Thông báo của tab cộng đồng
- `GENERAL`: Thông báo chung ở phía `client`
- `MAILBOX`: Thông báo cho phần hộp thư
- `ADMIN`: Thông báo cho `admin`

```data.message```: Tên thông báo gửi đi

```data.type```: Loại thông báo (Để `client` phân loại và xử lý từng loại thông báo)

### B. Các trường không bắt buộc:

```data.icon```: Tên icon map với `client`

```data.customJson```: `Data` để phía FE dùng trong một số trường hợp đặc biệt (Gửi dưới dạng `object`)

### 1.2 Publish mail đến service notify

Channel: ```SEND_MAIL```

Message: (Lưu ý: Message phải được gửi dưới dạng `stringify`)
```js
{
    "receivers": [
        "dungla2708@gmail.com"
    ],
    "type": "FORUM",
    "body": {
        "subject": "MXV NEWS Từ chối duyệt bài",
        "html": "<p>Đây là html</p>",
        "text": "Nội dung email",
        "attachments": [
            {
                "content": "Buffer or string",
                "filename": "example.txt"
            }
        ],
        "replyTo": "dungla2708@gmail.com"
    }
}
```

### A. Các trường bắt buộc:

```receivers```: Danh sách các email nhận thông báo này (gửi dưới dạng `email`)

```type```: Thuộc các loại thông báo dưới đây
- `FORUM`: Thông báo của tab cộng đồng
- `GENERAL`: Thông báo chung ở phía `client`
- `MAILBOX`: Thông báo cho phần hộp thư
- `ADMIN`: Thông báo cho `admin`

```body.subject```: Mail subject

```body.text```: Nội dung email (Độ ưu tiên sau `html`)

### B. Các trường không bắt buộc:

```body.html```: Nội dung email viết dưới dạng `html` (Độ ưu tiên cao hơn `text`)

```body.attachments```: Danh sách các file đính kèm trong `mail`

```body.replyTo```: Chỉ định mail trả lời

### 1.3 Publish event đến service notify

Channel: ```SEND_MESSAGE```

Message: (Lưu ý: Message phải được gửi dưới dạng `stringify`)
```js
{
    "receivers": ["60e2892ddf72ff0939c61c35"],
    "event": "LOGIN",
    "message": "Message example"
}
```

### A. Các trường bắt buộc

`receivers`: Danh sách các user nhận được event này

`event`: Đây là `event` để `client` listen

`message`: Nội dung `message` trả về `client`





