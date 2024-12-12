
# Hướng Dẫn Cài Đặt 

## **Yêu Cầu Hệ Thống**
!!! example "Yêu Cầu"
    - **Phần Cứng:**
        - Mạng: Kết nối internet ổn định, IP tĩnh nếu triển khai trên server.
        - CPU: Tối thiểu 4 nhân (khuyến nghị 8 nhân).
        - RAM: Tối thiểu 8GB (khuyến nghị 16GB).
        - Ổ cứng: Tối thiểu 50GB SSD.
    - **Phần Mềm:**
        - Hệ điều hành: Ubuntu 20.04+, CentOS 7/8, Windows 10/Server 2019+, hoặc macOS 11+.
        - Docker & Docker Compose: Phiên bản Docker Engine 20.10+, Compose 1.29+.
        - Node.js: Tối thiểu 14.x (khuyến nghị 16.x+).
        - Cơ sở dữ liệu: [MongoDB](https://www.mongodb.com/docs/manual/) cục bộ hoặc cloud với [MongoDB Atlas](https://www.mongodb.com/docs/atlas/).
    - **Công cụ bổ sung:** 
        - **Goong API Key**: Đăng ký và nhận API Key từ [Goong API](https://goong.io/).
        - **Firebase Project**: Tạo và cấu hình Firebase project để sử dụng dịch vụ thông báo đẩy (push notifications). <br>Cụ thể là 
    [FCM ](https://firebase.google.com/docs/cloud-messaging?hl=vi) và [Firestore](https://firebase.google.com/docs/firestore?hl=vi)

---
## **Các Bước Cài Đặt**

### Yêu Cầu 📋

Để cài đặt và chạy được dự án, trước tiên bạn cần phải cài đặt các công cụ bên dưới. Hãy thực hiện theo các hướng dẫn cài đặt sau, lưu ý chọn hệ điều hành phù hợp với máy tính:

-   [Docker-Installation](https://docs.docker.com/get-docker/)
-   [Docker-Compose-Installation](https://docs.docker.com/compose/install/)
-   [NodeJS v22-Installation](https://nodejs.org/en/download/)
-   [Budibase Cli-Installation](https://docs.budibase.com/docs/budibase-cli-setup)

**Cài đặt nhanh:** File `setup.sh` trong dự án của tôi
```bash
sh setup.sh
```

### 🔨 Cài Đặt

Trước hết, hãy khởi tạo dự án:

```bash
mkdir myProject
cd myProject

budi hosting --init
```

Tiếp theo, khởi chạy dự án:

```bash
budi hosting --start
```

Chạy dự án trên trình duyệt của bạn [http://localhost:10000](http://localhost:10000). Sau đó tạo đăng nhập và tạo ứng dụng.

Tải dự án về tại [link](https://github.com/FBeta-Hou/FBeta-Hou-App/blob/main/HoTroThienTai-export-1733664478310.tar.gz).

Sau đó, vào `Settings > Export/Import > Import app` rồi kéo thả file tài nguyên vào, sau đó ấn `Update`.

![Image title](assets/import-appp.png)

Tại đây bạn đã có thể thao tác với ứng dụng. Nếu muốn cài đặt dịch vụ của riêng mình để sử dụng. thì hãy đến với phần tiếp theo. 
## **Các Bước Cài Đặt Services **

### 1. Clone Repo

Trước tiên, clone dự án về máy của bạn:

```bash
git clone https://github.com/FBeta-Hou/FBeta-Services.git
```

### 2. Cài Đặt Các Phụ Thuộc

Chuyển vào thư mục dự án và chạy lệnh cài đặt các phụ thuộc:

```bash
cd FBeta-Services
npm install
```

### 3. Tạo File .env

Tạo một file .env trong thư mục gốc của dự án với nội dung sau:
```py linenums="1"
# Application Port
PORT=3000

# Map Configuration
# Thay thế các giá trị này bằng API keys thực tế từ Goong Maps API
Maptileskey=YourGoongMaptilesKeyHere
APIKey=YourGoongApiKeyHere
MONGO_URL=mongodb://localhost:27017/your_database_name

# Firebase Configuration
# Thay thế các thông tin này bằng các chi tiết Firebase thực tế
type=service_account
project_id=your-firebase-project-id
private_key_id=your-private-key-id
private_key="-----BEGIN PRIVATE KEY-----\nYourPrivateKeyHere\n-----END PRIVATE KEY-----\n"
client_email=firebase-adminsdk-abcde@your-firebase-project-id.iam.gserviceaccount.com
client_id=123456789012345678901
auth_uri=https://accounts.google.com/o/oauth2/auth
token_uri=https://oauth2.googleapis.com/token
auth_provider_x509_cert_url=https://www.googleapis.com/oauth2/v1/certs
client_x509_cert_url=https://www.googleapis.com/robot/v1/metadata/x509/firebase-adminsdk-abcde%40your-firebase-project-id.iam.gserviceaccount.com
universe_domain=googleapis.com

```

- Maptileskey và APIKey: Lấy từ trang [Goong API](https://goong.io/).
- MONGO_URL: Địa chỉ kết nối đến cơ sở dữ liệu MongoDB của bạn.
- Firebase Configuration: Tạo thông tin dịch vụ từ Firebase Console và thay thế vào đây. 
### 4. Chạy Ứng Dụng Cục Bộ 

Sau khi cấu hình xong, bạn có thể chạy ứng dụng trên máy cục bộ bằng lệnh sau:

```bash
npm start
```

### 5. Truy Cập Dịch Vụ

- Map Service sẽ chạy tại http://localhost:3000/map.
- Notification Service sẽ chạy tại http://localhost:3000/send-notification 

