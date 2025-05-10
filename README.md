# 📺 [HOT] Video 15p - Hướng Dẫn Chi Tiết Tạo 400GB VPS Windows  
**Admin SSH 24/7 MIỄN PHÍ Trên GITHUB | Không Thanh Toán**  
Hashtag: `#ltpython`  

---

## 🪜 Các bước cài đặt chi tiết

### 1. Cài đặt thư viện
```bash
sudo apt update
sudo apt install docker.io docker-compose
```bash
2. Cập nhật hệ thống
bash
Sao chép
Chỉnh sửa
sudo apt update
3. Cài đặt Docker & Docker Compose
bash
Sao chép
Chỉnh sửa
sudo apt install docker.io docker-compose -y
✅ Kiểm tra sau khi cài:

bash
Sao chép
Chỉnh sửa
docker -v
docker compose version
📂 Cấu trúc file docker-compose
Tạo file windows10.yml với nội dung:

yaml
Sao chép
Chỉnh sửa
version: "3.8"
services:
  windows:
    image: dockurr/windows
    container_name: windows
    environment:
      VERSION: "10"
      USERNAME: "MASTER"
      PASSWORD: "admin@123"
      RAM_SIZE: "8G"
      CPU_CORES: "4"
      DISK_SIZE: "600G"
      DISK2_SIZE: "200G"
    devices:
      - /dev/kvm
      - /dev/net/tun
    cap_add:
      - NET_ADMIN
    ports:
      - "8006:8006"
      - "3389:3389/tcp"
      - "3389:3389/udp"
    stop_grace_period: 2m
📌 Lưu ý: RAM_SIZE nên thấp hơn tổng RAM thật ít nhất 2GB để tránh lỗi thiếu RAM.

▶️ Chạy Windows trong Docker
bash
Sao chép
Chỉnh sửa
sudo docker-compose -f windows10.yml up -d
🐛 Các lỗi thường gặp & cách khắc phục
❌ Lỗi	✅ Cách sửa
no configuration file provided	Thêm -f windows10.yml vào lệnh
Cannot access /dev/kvm	Kiểm tra xem KVM đã bật chưa: ls -la /dev/kvm
permission denied on /dev/kvm	Thêm user vào nhóm kvm:
sudo usermod -aG kvm $USER && newgrp kvm
image not found	Kiểm tra kết nối mạng, thử chạy:
docker pull dockurr/windows
Không lưu được dữ liệu ổ đĩa sau khi restart	Mount volume hoặc sử dụng named volumes

📡 Tốc độ mạng trong VPS
Bạn có thể kiểm tra tốc độ mạng trong VPS tại trang:
👉 https://fast.com

📎 Tham khảo
🌐 Dockurr Windows - GitHub

📘 Tài liệu cài đặt Docker Engine

📗 Tài liệu Docker Compose

🧼 Gỡ cài đặt (nếu cần)
bash
Sao chép
Chỉnh sửa
sudo docker-compose -f windows10.yml down
sudo apt remove docker.io docker-compose
🔗 Link video hướng dẫn
🎥 https://youtu.be/febFLjCSNbU

