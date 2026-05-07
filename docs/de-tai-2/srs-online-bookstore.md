# SRS - Online Bookstore Management System

## 1. Gioi thieu

### 1.1 Muc dich
Tai lieu nay mo ta yeu cau cho he thong Quan ly Hieu sach Truc tuyen. Muc tieu la chuan hoa pham vi, actor, use case, yeu cau chuc nang va phi chuc nang de phuc vu phan tich, thiet ke va trien khai.

### 1.2 Pham vi he thong
He thong cung cap nen tang thuong mai dien tu cho san pham sach, ho tro:
- Khach hang tim kiem, xem chi tiet, them gio, dat hang, thanh toan, theo doi don.
- Quan tri vien quan ly danh muc sach, don hang, nguoi dung.
- Thu kho tiep nhan thong bao va xu ly chuan bi giao hang.

## 2. Mo ta tong the

### 2.1 Actor
- Khach hang (actor chinh)
- Quan tri vien (actor chinh)
- Thu kho (actor chinh)
- He thong thanh toan (actor phu)
- Dich vu email/SMS (actor phu)

### 2.2 Gia thiet va rang buoc
- Nguoi dung can co ket noi Internet.
- He thong yeu cau dang nhap de dat hang.
- Thanh toan la buoc bat buoc trong quy trinh dat hang.
- He thong can dong bo ton kho sau khi tao don thanh cong.

## 3. Yeu cau chuc nang

- FR-01: He thong phai cho phep khach hang dang ky tai khoan voi email hop le.
- FR-02: He thong phai cho phep khach hang dang nhap/dang xuat an toan.
- FR-03: He thong phai cho phep khach hang tim kiem sach theo ten, tac gia hoac the loai.
- FR-04: He thong phai hien thi danh sach sach co phan trang.
- FR-05: He thong phai hien thi chi tiet sach (gia, mo ta, ton kho, danh gia).
- FR-06: He thong phai cho phep khach hang them sach vao gio hang.
- FR-07: He thong phai cho phep cap nhat so luong/xoa sach khoi gio hang.
- FR-08: He thong phai cho phep khach hang dat hang khi gio hang co it nhat 1 san pham.
- FR-09: He thong phai include buoc thanh toan trong use case dat hang.
- FR-10: He thong phai kiem tra ton kho truoc khi xac nhan thanh toan.
- FR-11: He thong phai tao don hang voi trang thai ban dau "Cho xu ly" sau khi thanh toan thanh cong.
- FR-12: He thong phai gui email xac nhan sau khi tao don hang.
- FR-13: He thong phai cho phep khach hang xem lich su mua hang va chi tiet don.
- FR-14: He thong phai cho phep quan tri vien them/sua/xoa sach.
- FR-15: He thong phai cho phep quan tri vien xem/cap nhat trang thai don hang.
- FR-16: He thong phai thong bao cho thu kho khi co don moi.
- FR-17: He thong phai cho phep khach hang danh gia/binh luan sach sau khi mua.
- FR-18: He thong phai cho phep khach hang them sach vao danh sach yeu thich (extend khi xem chi tiet).

## 4. Yeu cau phi chuc nang

- NFR-01 (Bao mat): Mat khau phai duoc bam mot chieu (bcrypt/argon2), khong luu plaintext.
- NFR-02 (Phan quyen): Chi admin duoc quan ly sach/don; khach hang chi thao tac tai khoan cua minh.
- NFR-03 (Hieu nang): Thoi gian phan hoi trang chinh va tim kiem < 3 giay voi tai thong thuong.
- NFR-04 (Kha dung): Muc tieu uptime >= 99%.
- NFR-05 (Toan ven du lieu): Don hang va cap nhat ton kho phai toan ven giao dich.
- NFR-06 (Kha nang mo rong): Tach biet lop UI/Service/Repository/Domain de de bao tri.
- NFR-07 (Kha dung): Giao dien ro rang, thong diep loi de hieu, ho tro thiet bi di dong.
- NFR-08 (Theo doi): Ghi log cac loi thanh toan/gui email va hanh vi quan trong.

## 5. Tieu chi chap nhan tong quat

- Tat ca FR duoc truy vet toi use case va testcase.
- Luong dat hang xu ly duoc cac tinh huong: het hang, thanh toan that bai, loi gui email.
- Don hang tao thanh cong phai duoc hien thi ma don ngay ca khi email loi.
- Bao mat va phan quyen dat theo NFR.
