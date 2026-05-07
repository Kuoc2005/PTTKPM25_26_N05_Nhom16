# Actor - Use Case Matrix (De tai 2)

## Danh sach actor
- KH: Khach hang
- AD: Quan tri vien
- TK: Thu kho
- PAY: He thong thanh toan
- NOTI: Dich vu email/SMS

## Ma tran tuong tac

| Ma UC | Ten Use Case | KH | AD | TK | PAY | NOTI |
|---|---|---|---|---|---|---|
| UC-01 | Dang ky tai khoan | X |  |  |  |  |
| UC-02 | Dang nhap | X | X | X |  |  |
| UC-03 | Tim kiem va xem sach | X |  |  |  |  |
| UC-04 | Dat hang | X |  |  | X | X |
| UC-05 | Thanh toan | X |  |  | X |  |
| UC-06 | Theo doi don hang | X |  |  |  |  |
| UC-07 | Them vao yeu thich | X |  |  |  |  |
| UC-08 | Danh gia/Binh luan sach | X |  |  |  |  |
| UC-09 | Quan ly san pham |  | X |  |  |  |
| UC-10 | Quan ly don hang |  | X | X |  | X |
| UC-11 | Cap nhat trang thai don hang |  | X | X |  | X |
| UC-12 | Quan ly nguoi dung |  | X |  |  |  |
| UC-13 | Tao bao cao kinh doanh |  | X |  |  |  |
| UC-14 | Nhan thong bao don moi |  |  | X |  | X |
| UC-15 | Dong bo ton kho |  | X | X |  |  |

## Ghi chu quan he include/extend
- `UC-04 Dat hang` <<include>> `UC-05 Thanh toan` (bat buoc).
- `UC-03 Tim kiem va xem sach` <<extend>> `UC-07 Them vao yeu thich` (tuy chon).
