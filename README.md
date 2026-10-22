# Multi-Client-Broadcast & Game Vẽ Hình Đoán Chữ (Draw & Guess)
Chủ đề: Lập trình Multi-Client Server kết hợp Broadcast (TCP/WebSocket & MQTT Pub/Sub).

## Nội dung:
- Xây dựng một bảng vẽ chung trên web (hoặc ứng dụng mạng). Khi một Client chấm màu, vẽ nét cọ, hoặc gõ một từ khóa, Server lập tức Broadcast tọa độ và màu sắc đó tới tất cả các Client khác đang kết nối trong phòng.
- Mỗi thành viên sẽ thấy trực tiếp cấu hình 1-to-Many (Broadcast) hoạt động: 1 người vẽ, 50 người xem thấy nét vẽ nhảy realtime trên màn hình của từng thành viên.
- **Mới bổ sung — Chế độ Game Vẽ Hình Đoán Chữ (Draw & Guess):**
  - **Phân vai rõ ràng:** Người vẽ (Drawer) và Người đoán (Guesser).
  - **Bảo mật từ khóa:** Chỉ người vẽ nhận được từ khóa bí mật qua kênh riêng; người đoán tuyệt đối không nhận được từ khóa trước khi lượt kết thúc.
  - **Ngân hàng 30 từ khóa:** Đầy đủ 2 nhóm (Đồ vật/thiên nhiên và Khái niệm trừu tượng) kèm cơ chế chấp nhận từ đồng nghĩa/viết tắt hợp lệ.
  - **Random từ khóa độc lập:** Không lặp từ liên tiếp, dùng hết 30 từ trong một chu kỳ trước khi xáo trộn lại.
  - **Luân phiên theo FIFO:** Thứ tự người vẽ quay vòng công bằng: [An -> Bình -> Chi -> Dũng -> An...].
  - **Đồng hồ đếm ngược 90 giây:** Được đồng bộ realtime cho cả phòng; tự kết thúc khi hết giờ hoặc có người đoán đúng đầu tiên.
  - **Hệ thống điểm số:** Người đoán đúng đầu tiên nhận +10 điểm, Người vẽ nhận +5 điểm (nếu có người đoán đúng).
  - **Thử nghiệm linh hoạt:** Hỗ trợ kết nối nhiều tab/thiết bị qua MQTT hoặc dùng nút "Thêm người chơi giả lập (Bot)" để test ngay trên 1 tab trình duyệt.

## Hướng dẫn chạy và kiểm thử:
1. Mở file [index.html](file:///d:/LTM/Test-MQTT-main/index.html) bằng bất kỳ trình duyệt web nào (Chrome, Edge, Firefox).
2. Chuyển sang Tab 3 hoặc Tab 5 ("Game: Vẽ Hình Đoán Chữ").
3. Chạy kiểm thử logic tự động bằng Node.js:
   ```bash
   node test_game_logic.js
   ```

Mối liên hệ học phần: Minh họa cho Chương 5 (Multi-Client Server và cơ chế Broadcast / Pub-Sub)

