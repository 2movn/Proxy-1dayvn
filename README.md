# API Proxy 1dayvn
Hướng dẫn sử dụng API lấy proxy của 1dayvn.com.

Cần nhận API từ Admin hoặc mua từ website: https://proxy.1dayvn.com

## 1 - Proxy xoay 0 giây
- Đây là loại proxy có thể get liên tục. Mỗi lần Get sẽ trả về proxy khác nhau.
- Proxy sau khi get Live từ 30 phút ~8h.
- Get proxy không giới hạn số lần
- Proxy không giới hạn băng thông, dung lượng

### Cách thức lấy proxy qua API 
1. Phương thức:
`GET`

3. URL đích:
 ```https://proxy.1dayvn.com/api/premium/single-proxy?key=[API_KEY]```

4. JSon trả về:
   
```
{
  "status": "SUCCESS",
  "statusCode": 200,
  "data": {
    "ip": "117.5.212.137", // IP Proxy
    "port": 36009, //Port Proxy
    "geo_local": "VN", // Geo local
    "ms": "1742", // Milliseconds connect
    "type": "HTTP", // Type Proxy
    "ip_public": "117.0.115.73", // IP Public
    "created_at": "2023-11-04T15:39:03.000000Z",
    "updated_at": "2023-11-04T15:39:03.000000Z",
    "username": "byadmin", // User Proxy
    "password": "Xp51pgBB" // Password Proxy
  }
}
```

### Ví dụ get proxy:

#### Curl Example
```javascript
curl -X GET -H "Content-Type: application/json" https://proxy.1dayvn.com/api/premium/single-proxy?key=[API_KEY]
```

#### Python Example
```python
New_proxy = None
API = '' #API tại đây
headers_get = {
    'User-Agent': 'Mozilla/5.0 (1dayvn-AppDesktop) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36',
    "Content-Type": "application/json",
    "Accept": "application/json",
}
try:
    gettoken = requests.get(
        f'https://proxy.1dayvn.com/api/premium/single-proxy?key={API}',
        headers=headers_get)
    if gettoken.status_code == 200:
        datas = gettoken.json()
        data_ids = datas["data"]
        for item in data_ids:
            ip = item["ip"]
            port = item["port"]
            username = item["username"] if item["username"] else "None"
            password = item["password"] if item["password"] else "None"
            New_proxy = f'{ip}:{port}'
            if username and username != "None":
                New_proxy = f"{ip}:{port}:{username}:{password}"
    if gettoken.status_code == 400:
        print('API Đã hết hạn, Hoặc không chính xác\n'
except:
    print('Get Proxy erro')

print(New_proxy)
```

#### Nodejs - Axios Example
```javascript
const headers = {
  'User-Agent': 'Mozilla/5.0 (1dayvn-AppDesktop) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36'
};
let API = '' // API tại đây
let proxy = ''
try {
    const data_proxy = await axios.get(`https://proxy.1dayvn.com/api/premium/single-proxy?key=${API}`, {
    timeout: 10000,
    headers: headers,
    });
    if (data_proxy.status === 200) {
      raw_proxy = token_active.data;
      proxy =  `${raw_proxy.ip}:${raw_proxy.port}`
      if (raw_proxy.user){
        proxy = `${raw_proxy.ip}:${raw_proxy.port}:${raw_proxy.username}:${raw_proxy.password}:`
      }
    }
} catch (error) {
    console.log('Conect Server Erro', error)
}
console.log('proxy:', proxy)
```

### Tool hỗ trợ forward và tự động xoay
Công cụ hỗ trợ get, xoay proxy liên tục theo thời gian và forward proxy về dạng local.

- Link tải: [Tool Support](https://github.com/2movn/Proxy-1dayvn/releases/tag/1.0.0) (Mật khẩu nếu có: 599999)
- Video Hướng dẫn: [View Youtube](https://youtu.be/htko4rmIifM)

### Công cụ online:
- Công cụ Hỗ trợ lấy proxy: [Bắt đầu](https://1dayvn.com/help/get-proxy.html)
- API lấy proxy không `user:pass`: 
```
https://1dayvn.com/help/get-non.php?key=[API]
```

## 2 - Proxy Dân cư VN Fresh List
### Giới thiệu:
Dạng Fresh list là dạng danh sách và làm mới liên tục. Có nghĩa chúng tôi sẽ cấp cho bạn 1 danh sách proxy theo số lượng của gói. Nhưng proxy này sẽ được kiểm tra và làm mới (Thay thế) liên tục.
Thời gian làm mới 2 giờ/lần. Danh sách của bạn sẽ luôn được cập nhật đầy đủ số lượng.

(***Ghi chú***: Proxy này chỉ live từ 30 phút đến 8h)
### Cách sử dụng
Các bạn có thể sử dụng API được cung cấp để lấy danh sách với link API hoặc công cụ hỗ trợ kèm theo dưới đây.

Proxy có 2 định dạng `ip:port` và `ip:port:user:pass`


### 1. Tool hỗ trợ Lấy list Proxy
Công cụ hỗ trợ get Fresh list từ server về. Đồng thời giúp các bạn check live proxy.
#### Chức năng:
1. Hỗ trợ lấy Proxy list về nhanh chóng.
2. Hỗ trợ kiểm tra kết nối proxy.
3. Hỗ trợ lọc trùng và xuât tệp `.txt` và `exel`.

Công cụ có thống kê rõ ràng cho từng proxy vì vậy đây là một công cụ hữu ích cần thiết cho bạn.

#### Tải về:
- Link tải: [Tool Support](https://drive.google.com/file/d/1Vr_KDPc2vec23ypm_u9WcaF4A0HT5zYe/view?usp=sharing) (Mật khẩu nếu có: 599999)
- Video Hướng dẫn: [View Youtube](https://youtu.be/qwV9MiZQIxM)


## 3. Công cụ online:
- Công cụ Hỗ trợ chuyển định dạng `ip:port:user:pass` thành `user:pass@ip:port`: [Bắt đầu](https://1dayvn.com/help/cover-type.html)
- Công cụ Hỗ trợ chuyển định dạng `host:port:user:pass` thành `ip:port:user:pass`: [Bắt đầu](https://1dayvn.com/help/cover-ip.html)

# Liên hệ:
- Facebook: https://www.facebook.com/2movn
- TeleGram: https://t.me/mmovnofflical
