# diemTrungBinhHCMUS-2022
Update tính điểm trung bình môn học và chuyên ngành HCMUS từ năm 2022 - Vì portal đã sửa có thêm điểm "VẮNG" cho các học phần không tham dự thi.
B1: Vào Portal phần kết tra cứu quả học tập -> Tại phần năm học chọn tất cả
B2: Nhấn chuộc phải -> Chọn Inspect trang hiển thị kết quả điểm thi vừa hiển thị
B3: Tại Console copy đoạn code dưới đây và dán vào -> Nhấn Enter: (Kết quả hiển thị là số tín chỉ đã tích luỹ và điểm trung bình cuối cùng.) 

var tinchi = document.querySelectorAll("td:nth-child(3)");
var monhoc = document.querySelectorAll("td:nth-child(2)");
var diem = document.querySelectorAll("td:nth-child(6)");
var diemtren = 0,
diemduoi = 0;
var diemSPtren = 0,
diemSPduoi = 0;
for (var i = 1; i < tinchi.length; i++) {
if (
monhoc[i].innerText.includes("Thể dục") ||
monhoc[i].innerText.includes("Anh văn") ||
monhoc[i].innerText.includes("Giáo dục") ||
Number(diem[i].innerText) < 5|| diem[i].innerText.includes("Vắng")
) {
continue;
} else if (monhoc[i].innerText.includes("CSC")) {
//sửa CSC nếu muốn tính điểm nhóm môn khác, vd PHY, MTH,...
diemSPtren += Number(tinchi[i].innerText) * Number(diem[i].innerText);
diemSPduoi += Number(tinchi[i].innerText);
}
diemtren += Number(tinchi[i].innerText) * Number(diem[i].innerText);
diemduoi += Number(tinchi[i].innerText);
}
console.log("Tong tin chi : " + diemduoi);
console.log("Diem trung binh : " + diemtren / diemduoi);
console.log("Tong tin chi mon SP: " + diemSPduoi);
console.log("Diem trung binh SP: " + diemSPtren / diemSPduoi);
