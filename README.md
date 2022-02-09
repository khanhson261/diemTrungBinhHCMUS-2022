# diemTrungBinhHCMUS-2022
Update tính điểm trung bình môn học và chuyên ngành HCMUS từ năm 2022 vì portal đã sửa có thêm điểm "VẮNG" cho các học phần không tham dự thi.<br>
B1: Vào Portal phần kết tra cứu quả học tập -> Tại phần năm học chọn tất cả <br>
B2: Nhấn chuộc phải -> Chọn Inspect trang hiển thị kết quả điểm thi vừa hiển thị <br>
B3: Tại Console copy đoạn code dưới đây và dán vào -> Nhấn Enter: (Kết quả hiển thị là số tín chỉ đã tích luỹ và điểm trung bình cuối cùng.) <br>

var tinchi = document.querySelectorAll("td:nth-child(3)"); <br>
var monhoc = document.querySelectorAll("td:nth-child(2)"); <br>
var diem = document.querySelectorAll("td:nth-child(6)"); <br>
var diemtren = 0, <br>
diemduoi = 0;<br>
var diemSPtren = 0,<br>
diemSPduoi = 0;<br>
for (var i = 1; i < tinchi.length; i++) {<br>
if (<br>
monhoc[i].innerText.includes("Thể dục") ||<br>
monhoc[i].innerText.includes("Anh văn") ||<br>
monhoc[i].innerText.includes("Giáo dục") ||<br>
Number(diem[i].innerText) < 5|| diem[i].innerText.includes("Vắng")<br>
) {<br>
continue;<br>
} else if (monhoc[i].innerText.includes("CSC")) {<br>
//sửa CSC nếu muốn tính điểm nhóm môn khác, vd PHY, MTH,...<br>
diemSPtren += Number(tinchi[i].innerText) * Number(diem[i].innerText);<br>
diemSPduoi += Number(tinchi[i].innerText);<br>
}<br>
diemtren += Number(tinchi[i].innerText) * Number(diem[i].innerText);<br>
diemduoi += Number(tinchi[i].innerText);<br>
}<br>
console.log("Tong tin chi : " + diemduoi);<br>
console.log("Diem trung binh : " + diemtren / diemduoi);<br>
console.log("Tong tin chi mon SP: " + diemSPduoi);<br>
console.log("Diem trung binh SP: " + diemSPtren / diemSPduoi);<br>
