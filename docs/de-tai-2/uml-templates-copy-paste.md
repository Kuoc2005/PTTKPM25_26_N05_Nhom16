# Bo template UML (copy-paste)

Tai lieu nay cung cap mau nhanh de nhom copy-paste vao bao cao PTTKPM va trien khai ve UML.

---

## 1) Template Use Case Scenario (1 trang / 1 UC)

> Sao chep khoi nay cho tung use case (UC-01, UC-02, ...).

```text
TEN USE CASE: [Ten use case]
MA SO: [UC-xx]

ACTOR CHINH:
- [Actor chinh]

ACTOR PHU:
- [Actor phu 1]
- [Actor phu 2]

MUC TIEU:
- [Actor dat duoc gi sau khi UC thanh cong]

DIEU KIEN TIEN QUYET:
- [Precondition 1]
- [Precondition 2]

KICH HOAT (TRIGGER):
- [Su kien bat dau use case]

LUONG CHINH:
1. [Buoc 1]
2. [Buoc 2]
3. [Buoc 3]
4. [Buoc 4]
5. [Buoc 5]
6. [Buoc 6]

LUONG THAY THE:
- 3a. [Dieu kien]
  1. [Xu ly thay the]
  2. [Ket qua]
- 5a. [Dieu kien]
  1. [Xu ly thay the]
  2. [Ket qua]

LUONG NGOAI LE:
- E1. [Loi he thong / timeout / mat ket noi]
  1. [He thong xu ly]
  2. [Thong bao cho nguoi dung]

HAU DIEU KIEN:
- [Du lieu duoc luu/cap nhat]
- [Trang thai moi]

BUSINESS RULE LIEN QUAN:
- [BR-01...]
- [BR-02...]
```

---

## 2) Template Scenario mau - UC-04 Dat hang (da dien san)

```text
TEN USE CASE: Dat hang
MA SO: UC-04

ACTOR CHINH:
- Khach hang

ACTOR PHU:
- DonHangService
- SachRepository
- He thong thanh toan
- Dich vu Email

MUC TIEU:
- Tao don hang thanh cong va nhan ma don hang.

DIEU KIEN TIEN QUYET:
- Khach hang da dang nhap.
- Gio hang co it nhat 1 san pham.
- San pham con ton kho.

KICH HOAT (TRIGGER):
- Khach hang nhan nut "Dat hang" tai trang gio hang.

LUONG CHINH:
1. Khach hang vao gio hang va chon Dat hang.
2. He thong hien thi form thong tin giao hang.
3. Khach hang nhap dia chi, so dien thoai va chon phuong thuc thanh toan.
4. He thong kiem tra ton kho tung san pham.
5. He thong tinh tong tien (tam tinh + phi ship - giam gia neu co).
6. Khach hang xac nhan don va tien hanh thanh toan.
7. He thong tao don hang, cap nhat ton kho.
8. He thong gui email xac nhan va hien thi ma don hang.
9. Thu kho nhan thong bao de chuan bi hang.

LUONG THAY THE:
- 4a. Sach het hang:
  1. He thong thong bao san pham het hang.
  2. He thong goi y sach tuong tu hoac cho phep xoa khoi gio.
- 6a. Thanh toan that bai:
  1. He thong thong bao that bai.
  2. Khach hang duoc thu lai hoac doi phuong thuc thanh toan.

LUONG NGOAI LE:
- E1. Loi gui email:
  1. He thong van luu don hang thanh cong.
  2. He thong ghi log loi email va hien thi ma don tren man hinh.

HAU DIEU KIEN:
- Don hang duoc tao voi trang thai "Cho xu ly".
- Ton kho duoc cap nhat.
- Lich su mua hang duoc luu.
```

---

## 3) Template Class Diagram khoi tao (de tai hieu sach)

> Danh sach nay dung de ve nhanh Class Diagram ban dau, sau do bo sung thuoc tinh/phuong thuc khi doi chieu Sequence.

```text
<<entity>> User
- id: Long
- name: String
- email: String
- passwordHash: String
- role: UserRole
+ login(email, password): boolean
+ updateProfile(data): void

<<entity>> Book
- id: Long
- sku: String
- title: String
- author: String
- price: Decimal
- stockQty: int
+ isInStock(qty): boolean
+ decreaseStock(qty): void

<<entity>> Cart
- id: Long
- userId: Long
- items: List<CartItem>
+ addItem(bookId, qty): void
+ removeItem(bookId): void
+ calculateSubtotal(): Decimal

<<entity>> CartItem
- bookId: Long
- qty: int
- unitPrice: Decimal
+ lineTotal(): Decimal

<<entity>> Order
- id: Long
- userId: Long
- status: OrderStatus
- totalAmount: Decimal
- shippingAddress: String
- createdAt: DateTime
+ calculateTotal(): Decimal
+ changeStatus(newStatus): void

<<entity>> OrderItem
- id: Long
- orderId: Long
- bookId: Long
- qty: int
- unitPrice: Decimal
+ lineTotal(): Decimal

<<entity>> Payment
- id: Long
- orderId: Long
- method: PaymentMethod
- status: PaymentStatus
- transactionRef: String
+ authorize(amount): boolean
+ capture(): boolean

<<service>> OrderService
+ placeOrder(userId, checkoutRequest): Order
+ validateStock(cart): boolean
+ updateOrderStatus(orderId, status): void

<<service>> PaymentService
+ processPayment(orderId, paymentRequest): PaymentResult

<<service>> InventoryService
+ checkAvailability(bookId, qty): boolean
+ reserveStock(orderItems): void
+ releaseStock(orderItems): void

<<repository>> BookRepository
+ findById(id): Book
+ save(book): void

<<repository>> OrderRepository
+ save(order): Order
+ findById(id): Order
+ findByUser(userId): List<Order>
```

### Quan he goi y de ve

```text
User 1 --- 0..* Order
User 1 --- 1 Cart
Cart 1 --- 1..* CartItem
Order 1 --- 1..* OrderItem (composition)
Book 1 --- 0..* OrderItem
Book 1 --- 0..* CartItem
OrderService --> OrderRepository
OrderService --> BookRepository
OrderService --> PaymentService
OrderService --> InventoryService
```

---

## 4) Template Sequence Diagram - UC Dat hang

> Copy khoi message nay vao phan mo ta Sequence hoac lam script de ve nhanh.

```text
Actor: KhachHang
Lifelines (trai -> phai):
KhachHang -> CheckoutUI -> OrderService -> BookRepository -> PaymentGateway -> OrderRepository -> EmailService

1. KhachHang -> CheckoutUI: submitOrder(checkoutForm)
2. CheckoutUI -> OrderService: placeOrder(userId, cart, shippingInfo, paymentInfo)
3. OrderService -> BookRepository: checkStock(cartItems)
4. BookRepository --> OrderService: stockResult

alt [Con hang]
  5. OrderService -> PaymentGateway: charge(totalAmount, paymentInfo)
  6. PaymentGateway --> OrderService: paymentSuccess(txnRef)
  7. OrderService -> OrderRepository: save(order + orderItems)
  8. OrderRepository --> OrderService: savedOrder(orderId)
  9. OrderService -> EmailService: sendOrderConfirmation(orderId, email)
  10. EmailService --> OrderService: sent/failed
  11. OrderService --> CheckoutUI: orderSuccess(orderId)
  12. CheckoutUI --> KhachHang: showOrderCode(orderId)

else [Het hang]
  A1. OrderService --> CheckoutUI: outOfStock(bookList)
  A2. CheckoutUI --> KhachHang: hien thi thong bao + goi y

else [Thanh toan that bai]
  B1. PaymentGateway --> OrderService: paymentFailed(reason)
  B2. OrderService --> CheckoutUI: paymentFailed(retryable=true)
  B3. CheckoutUI --> KhachHang: cho phep thu lai/doi phuong thuc
end
```

---

## 5) Template Activity Diagram - Xu ly don hang

```text
Start
-> [KhachHang] Nhap thong tin giao hang
-> [HeThong] Kiem tra hop le du lieu
-> (Hop le?)
   - No  -> Hien thi loi -> End
   - Yes -> Kiem tra ton kho
-> (Du ton kho?)
   - No  -> Thong bao het hang -> End
   - Yes -> Tao yeu cau thanh toan
-> (Thanh toan thanh cong?)
   - No  -> Thong bao that bai, cho phep thu lai -> End
   - Yes -> Tao don hang
-> Cap nhat ton kho
-> Gui email xac nhan
-> Hien thi ma don hang
-> End
```

---

## 6) Template State Machine - Don hang

```text
[*] -> ChoXuLy
ChoXuLy -> DaXacNhan: xacNhanDon [paymentSuccess]
ChoXuLy -> DaHuy: huyDon [requestedByUser]
DaXacNhan -> DangDongGoi: batDauDongGoi [warehouseAccepted]
DangDongGoi -> DangGiao: banGiaoDonViVanChuyen
DangGiao -> GiaoThanhCong: giaoThanhCong
DangGiao -> GiaoThatBai: giaoThatBai
GiaoThatBai -> DangGiao: giaoLai [retry < 3]
GiaoThatBai -> DaHuy: huySauThatBai [retry >= 3]
GiaoThanhCong -> [*]
DaHuy -> [*]
```

---

## 7) Checklist nhanh truoc khi nop

- Use Case Diagram: du actor/use case, co system boundary, include/extend dung.
- Scenario: moi UC co pre/main/alternative/exception/post.
- Class: co thuoc tinh + method + multiplicity + stereotype.
- Sequence: dung thu tu lifeline theo tang, co return, co alt/opt/loop.
- Activity: co decision, merge, swimlane ro trach nhiem.
- State: co initial/final, guard, trigger hop ly.
