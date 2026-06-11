
# Detecting SQL injection vulnerabilites

- **How to detect SQL injection vulnerabilities**
    - Có thể phát hiện **SQL Injection (SQLi)** bằng cách **kiểm tra thủ công** các điểm nhập dữ liệu (input).
    - Các cách kiểm tra phổ biến:
    1. **Nhập dấu `'` (single quote)**
        - Nếu xuất hiện lỗi → có thể có SQLi
    2. **Thử cú pháp SQL đặc biệt**
        - So sánh phản hồi khi giá trị:
            - Đúng (giữ nguyên logic)
            - Sai (thay đổi logic)
    3. **Điều kiện Boolean**
        - Ví dụ:
            - `OR 1=1` (luôn đúng)
            - `OR 1=2` (luôn sai)
        - So sánh phản hồi để phát hiện khác biệt
    4. **Time-based payload**
        - Gửi câu lệnh gây **delay**
        - Nếu phản hồi chậm → có thể bị SQLi
    5. **OAST payload (Out-of-band)**
        - Gây tương tác mạng bên ngoài
        - Theo dõi xem có request bất thường không
    - Ngoài kiểm tra thủ công:
        - Có thể dùng công cụ như **Burp Scanner** để phát hiện nhanh và hiệu quả hơn
    
    👉 Nói ngắn gọn:
    
    SQLi được phát hiện bằng cách gửi các payload đặc biệt và quan sát sự thay đổi trong phản hồi hệ thống.
    
- **SQL injection in different parts of the query**
    - Phần lớn lỗ hổng **SQL Injection (SQLi)** xảy ra trong:
        - **mệnh đề WHERE** của câu lệnh `SELECT` (trường hợp phổ biến nhất)
    - Tuy nhiên, SQLi có thể xuất hiện **ở nhiều vị trí khác trong truy vấn**, không chỉ riêng WHERE:
    1. **UPDATE**
        - Trong **giá trị cập nhật**
        - Hoặc trong **WHERE clause**
    2. **INSERT**
        - Trong **giá trị được chèn vào**
    3. **SELECT**
        - Trong **tên bảng hoặc tên cột**
    4. **ORDER BY**
        - Trong phần **sắp xếp dữ liệu**
    
    👉 Nói ngắn gọn:
    
    SQLi không chỉ xảy ra ở WHERE mà có thể xuất hiện **ở bất kỳ đâu trong câu truy vấn SQL**, tùy vào cách ứng dụng xử lý dữ liệu đầu vào.
