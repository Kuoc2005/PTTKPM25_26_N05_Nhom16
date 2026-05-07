# Kich ban Use Case chi tiet

## UC-04 - Dat hang

- **Ma so**: UC-04
- **Actor chinh**: Khach hang
- **Actor phu**: DonHangService, SachRepository, He thong thanh toan, Dich vu email
- **Dieu kien tien quyet**:
  - Khach hang da dang nhap
  - Gio hang co it nhat 1 san pham
  - San pham con ton kho
- **Hau dieu kien**:
  - Don hang duoc tao voi trang thai `Cho xu ly`
  - Ton kho duoc cap nhat
  - Lich su mua hang duoc luu

### Luong chinh
1. Khach hang vao gio hang va nhan "Dat hang".
2. He thong hien thi form thong tin giao hang.
3. Khach hang nhap dia chi va chon phuong thuc thanh toan.
4. He thong kiem tra ton kho tung san pham.
5. He thong tinh tong tien (bao gom phi ship).
6. Khach hang xac nhan va thuc hien thanh toan.
7. He thong tao don hang va gui email xac nhan.
8. Thu kho nhan thong bao de chuan bi hang.

### Luong thay the
- **4a - Het hang**: He thong thong bao sach het hang va de xuat sach tuong tu.
- **6a - Thanh toan that bai**: He thong cho phep thu lai hoac doi phuong thuc thanh toan.
- **7a - Loi email**: He thong ghi log loi, van hien thi ma don hang tren giao dien.

### Luong ngoai le
- **E1 - Mat ket noi cong thanh toan**: He thong danh dau giao dich loi tam thoi, thong bao nguoi dung thu lai sau.
- **E2 - Du lieu gio hang thay doi dong thoi**: He thong dong bo gio, yeu cau khach hang xac nhan lai.

---

## UC-03 - Tim kiem va xem chi tiet sach

- **Ma so**: UC-03
- **Actor chinh**: Khach hang
- **Dieu kien tien quyet**: He thong dang hoat dong, du lieu sach san sang
- **Hau dieu kien**: Ket qua tim kiem hien thi dung dieu kien loc

### Luong chinh
1. Khach hang nhap tu khoa tim kiem hoac chon bo loc.
2. He thong truy van danh muc sach theo dieu kien.
3. He thong hien thi danh sach sach co phan trang.
4. Khach hang chon 1 sach de xem chi tiet.
5. He thong hien thi thong tin sach, gia, ton kho, danh gia.

### Luong thay the
- **1a - Khong nhap tu khoa**: He thong hien thi danh sach sach moi/pho bien.
- **2a - Khong co ket qua**: He thong thong bao "Khong tim thay sach phu hop".

### Luong ngoai le
- **E1 - Loi truy van CSDL**: He thong thong bao loi tam thoi va ghi log.

### Quan he
- `UC-03` <<extend>> `UC-07 Them vao yeu thich`.

---

## UC-10 - Quan ly don hang

- **Ma so**: UC-10
- **Actor chinh**: Quan tri vien
- **Actor phu**: Thu kho, Dich vu email/SMS
- **Dieu kien tien quyet**: Admin da dang nhap voi quyen hop le
- **Hau dieu kien**: Trang thai don duoc cap nhat va thong bao duoc gui

### Luong chinh
1. Admin vao trang danh sach don hang.
2. He thong hien thi cac don theo bo loc trang thai/thoi gian.
3. Admin mo chi tiet 1 don.
4. Admin cap nhat trang thai (Cho xu ly -> Dang giao -> Hoan tat).
5. He thong luu lich su thay doi va gui thong bao cho khach hang.
6. Thu kho nhan thong tin de tiep tuc xu ly neu can.

### Luong thay the
- **4a - Don bi huy**: He thong khoi phuc ton kho cho cac san pham lien quan.
- **5a - Loi gui thong bao**: He thong luu trang thai don, danh dau thong bao cho hang doi gui lai.

### Luong ngoai le
- **E1 - Admin khong du quyen**: He thong tu choi truy cap va ghi nhat ky bao mat.
