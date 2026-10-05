Phân tích nguyên nhân lỗi:

Lỗi sai cơ chế hàng đợi (Logic Error): Mã nguồn hiện tại đang sử dụng phương thức waitingQueue.pop(). Phương thức này lấy ra phần tử nằm ở cuối mảng (LIFO - Vào sau ra trước), điều này dẫn đến việc chiếc xe đến muộn nhất lại được ưu tiên vào sạc trước, gây sai nghiệp vụ điều phối của trạm sạc. Cần thay bằng phương thức shift() để lấy phần tử ở đầu mảng (FIFO - Vào trước ra trước).

Lỗi vượt quá chỉ số mảng (Out-of-bounds / Off-by-one Error): Vòng lặp for tính tổng đang sử dụng điều kiện i <= completedSessionsKwh.length. Với mảng có 4 phần tử, chỉ số (index) hợp lệ chỉ từ 0 đến 3. Khi i = 4, hệ thống truy cập vào completedSessionsKwh[4] sẽ trả về undefined. Phép toán cộng một số với undefined (totalKwh += undefined) sẽ sinh ra kết quả NaN (Not a Number), làm hỏng toàn bộ dữ liệu doanh thu bên dưới. Cần sửa điều kiện thành i < completedSessionsKwh.length.
