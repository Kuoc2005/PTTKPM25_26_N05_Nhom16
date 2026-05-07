# Kien truc he thong va huong dan tuan 1-5

## 1) Kien truc phan tang (4-tier)

He thong ap dung kien truc 4 tang de tach biet trach nhiem va de mo rong:

- **Presentation Layer (UI)**: Blade views, route handlers, form validation, thong bao loi.
- **Service Layer (Business Logic)**: Xu ly nghiep vu dat hang, thanh toan, cap nhat trang thai don.
- **Repository Layer (Data Access)**: Truy cap du lieu products/orders/users/comments, dong goi truy van.
- **Domain Layer (Entity)**: Cac thuc the nghiep vu: Sach, DonHang, NguoiDung, GioHang, DanhGia.

## 2) Design patterns ap dung

### 2.1 Singleton Pattern - Database connection
- Muc dich: dam bao quan ly ket noi CSDL nhat quan.
- Ap dung trong Laravel: su dung service container/config/database de giam tao ket noi trung lap.

### 2.2 Factory Pattern - Tao doi tuong sach linh hoat
- Muc dich: tao nhieu loai sach (`SachGiay`, `SachDienTu`, `Audiobook`) theo cung mot giao dien.
- Loi ich: mo rong loai sach moi ma khong sua nhieu logic o service.

### 2.3 Observer Pattern - Thong bao su kien
- Muc dich: phat su kien khi don thay doi trang thai.
- Vi du: Don hang duoc tao/cap nhat -> gui email cho khach + thong bao thu kho.

## 3) Lo trinh trien khai tuan 1-5 (de xuat thuc thi tren project hien tai)

## Tuan 1 - Phan tich yeu cau
- Chot actor va 12-15 use case.
- Hoan tat SRS (FR/NFR/rang buoc/ma tran actor-use case).
- San pham nop:
  - `docs/de-tai-2/srs-online-bookstore.md`
  - `docs/de-tai-2/actor-usecase-matrix.md`

## Tuan 2 - Use Case diagram va kich ban
- Ve Use Case tong the va xac dinh include/extend.
- Hoan tat 3-4 kich ban use case quan trong (bao gom luong thay the + ngoai le).
- San pham nop:
  - `docs/de-tai-2/use-case-scenarios.md`
  - File diagram (`.drawio`/`.png`/`.pdf`)

## Tuan 3 - Class design va code skeleton
- Trich xuat lop tu kich ban: `Book`, `Order`, `OrderItem`, `Payment`, `InventoryService`.
- Chuan hoa quan he va bo sung service/repository interface ro rang.
- Tao/hoan thien skeleton:
  - `app/Services/OrderService.php`
  - `app/Repositories/BookRepositoryInterface.php`
  - `app/Repositories/OrderRepositoryInterface.php`

## Tuan 4 - Sequence diagram va UI mockup
- Ve sequence cho:
  - Dat hang + thanh toan
  - Cap nhat trang thai don hang
- Hoan thien mockup 4-5 man hinh: Home, Product detail, Cart, Checkout, Order tracking.
- Doi chieu ten method giua diagram va class code.

## Tuan 5 - State machine va activity
- Xac dinh vong doi `DonHang`: `PENDING -> CONFIRMED -> PACKING -> SHIPPING -> COMPLETED/CANCELLED`.
- Cai dat enum trang thai va validation chuyen trang thai.
- Them unit test cho state transitions.

## 4) Mapping nhanh voi code hien tai (Laravel)

- `app/Http/Controllers/FrontendController.php`: luong user front-site, gio hang, checkout.
- `app/Models/order.php`: thuc the don hang can bo sung state enum ro rang.
- `app/Http/Controllers/admin/orderController.php`: nghiep vu admin quan ly don.
- `app/Mail/*`: kenh thong bao email theo observer/event.

## 5) Tieu chi danh gia ket qua

- Tai lieu day du theo moi tuan, trace tu use case den code.
- Dat hang hoat dong on dinh voi cac luong loi (het hang/that bai thanh toan/email loi).
- Co test cho logic chuyen trang thai don va cap nhat ton kho.
