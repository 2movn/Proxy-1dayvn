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

### Curl Example
```javascript
curl -X GET -H "Content-Type: application/json" https://proxy.1dayvn.com/api/premium/single-proxy?key=[API_KEY]
```

### Python Example
```python
New_proxy = None
API = '' #API tại đây
headers_get = {
    'User-Agent': 'Mozilla/5.0 (1proxy-AppDesktop) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36',
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

### Nodejs - Axios Example
```javascript
const headers = {
  'User-Agent': 'Mozilla/5.0 (App Gologin Auto) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36'
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
        proxy = `${raw_proxy.ip}:${raw_proxy.ip}:${raw_proxy.ip}:${raw_proxy.ip}:`
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

## 2 - Proxy Datacenter VN Fresh List
### Cách sử dụng
(Đang cập nhật)

### Giới thiệu:
(Đang cập nhật)

### 1. Tool hỗ trợ forward và tự động xoay
Công cụ hỗ trợ get Fresh list từ server về. Đồng thời giúp các bạn check live proxy.
#### Chức năng:
1. Hỗ trợ lấy Proxy list về nhanh chóng.
2. Hỗ trợ kiểm tra kết nối proxy.
3. Hỗ trợ lọc trùng và xuât tệp `.txt` và `exel`.

Công cụ có thống kê rõ ràng cho từng proxy vì vậy đây là một công cụ hữu ích cần thích cho bạn.


### 2. Công cụ online:
- Công cụ Hỗ trợ chuyển định dạng `ip:port:user:pass` thành `user:pass@ip:port`: [Bắt đầu](https://api.2movn.com/cover-type.html)
- Công cụ Hỗ trợ chuyển định dạng `host:port:user:pass` thành `ip:port:user:pass`: [Bắt đầu](https://api.2movn.com/cover-ip.html)

  
#### Tải về:
- Link tải: [Tool Support](https://drive.google.com/file/d/1Vr_KDPc2vec23ypm_u9WcaF4A0HT5zYe/view?usp=sharing) (Mật khẩu nếu có: 599999)
- Video Hướng dẫn: [View Youtube](https://youtu.be/qwV9MiZQIxM)

# Liên hệ:
- Facebook: https://www.facebook.com/2movn
- TeleGram: https://t.me/mmovnofflical
