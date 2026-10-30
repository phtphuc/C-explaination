// C++ · Arrays · Functions · File I/O

# Nhập mảng số nguyên rồi ghi ra file

Chạy từng bước với input `N = 5`, mảng `{3, 1, 4, 1, 5}`: nhập mảng bằng `inputIntArray`, mở file bằng `ofstream`, ghi bằng `saveIntArray`, rồi đóng file.

Dùng phím ← → hoặc Space để chuyển · F: toàn màn hình · A: hiện hết bước

## Nội dung

· bấm vào mục để đi tới

**01**Đề bài & ví dụ

**02**Phân tích: chia thành hàm

**03**main – khai báo & gọi hàm

**04**inputIntArray – chạy từng bước

**05**Mở file bằng ofstream

**06**saveIntArray – chạy từng bước

**07**Đóng file & kết thúc

**08**Lưu ý & tóm tắt

BƯỚC 1

## Đề bài & ví dụ input / output

### Yêu cầu

- Nhập số phần tử **n**, rồi nhập **n** số nguyên vào mảng.
- Ghi **n** và các phần tử ra file `D:\intarray-output.txt`.
- Tổ chức bằng **hàm**: `inputIntArray` và `saveIntArray`.

Mảng khai báo dài 100 ô, nhưng chương trình chỉ dùng **n** ô đầu tiên.

Màn hình khi chạy (N = 5)

Number of elements: 5 a\[0\]: 3 a\[1\]: 1 a\[2\]: 4 a\[3\]: 1 a\[4\]: 5

Chữ màu vàng là dữ liệu người dùng gõ vào.

Nội dung file sau khi chạy

5 3 1 4 1 5

BƯỚC 2

## Phân tích: chia bài toán thành các hàm

| Hàm | Tham số | Nhiệm vụ |
| --- | --- | --- |
| `main` | argc, argv (không dùng) | Khai báo mảng và n, gọi hàm, mở và đóng file |
| `inputIntArray` | `int a[]`, `int &n` | Đọc n, rồi đọc n phần tử vào mảng |
| `saveIntArray` | `ofstream &f`, `int a[]`, `int n` | Ghi n và các phần tử ra file |

### int &n

Truyền tham chiếu, nên hàm sửa được n của main.

### int a\[\]

Thực chất là con trỏ tới phần tử đầu, mảng không bị sao chép.

### ofstream &f

Luồng file không sao chép được, nên bắt buộc truyền tham chiếu.

BƯỚC 3

## `main` – khai báo và gọi hàm

main.cpp

hàmmain

n?

a\[0\]?

a\[1\]?

a\[2\]?

a\[3\]?

a\[99\]…

Mảng `a[100]` có 100 ô, nhưng chỉ dùng n ô đầu.

Nhấn → để chạy từng bước.

BƯỚC 4

## `inputIntArray` – chạy từng bước

array.cpp

Number of elements: 5 a\[0\]: 3 a\[1\]: 1 a\[2\]: 4 a\[3\]: 1 a\[4\]: 5

hàmmain

n?

i–

a\[0\]?

a\[1\]?

a\[2\]?

a\[3\]?

a\[4\]?

a\[5\]…

Chỉ 5 ô đầu được dùng. Các ô a\[5\] đến a\[99\] vẫn chưa dùng.

Nhấn → để chạy từng bước.

BƯỚC 5

## Mở file bằng `ofstream`

main.cpp (phần mở và ghi file)

fchưa khai báo

**① ofstream f;**

Đối tượng luồng ghi file. Chưa liên kết với file nào.

**② f.open("D:\\\\intarray-output.txt")**

Tạo hoặc ghi đè file. Trong chuỗi C++, hai dấu \\\\ là một dấu \\ thật.

**③ if(!f.is_open())**

Mở được thì điều kiện sai, bỏ qua dòng in lỗi và rẽ sang else.

Nhấn → để chạy từng bước.

BƯỚC 6

## `saveIntArray` – ghi n và các phần tử

array.cpp

File D:\\intarray-output.txt

5 3 1 4 1 5

n5

i–

a\[0\]3

a\[1\]1

a\[2\]4

a\[3\]1

a\[4\]5

Nhấn → để chạy từng bước.

BƯỚC 7

## Đóng file & kết thúc

main.cpp (cuối hàm)

**f.close()**

Đẩy dữ liệu xuống đĩa, giải phóng tài nguyên của file.

**return 0;**

Chương trình kết thúc thành công.

Nhấn → để chạy từng bước.

fđang mở

Nội dung file sau khi chạy

5 3 1 4 1 5

Dòng 2 có dấu cách thừa ở cuối. Khi đọc lại bằng cin, dấu cách này không gây lỗi.

TỔNG KẾT

## Lưu ý & tóm tắt

### Mảng cố định

Code không kiểm tra n. Nếu n > 100, vòng lặp ghi ra ngoài mảng.

### Không kiểm tra cin

Nhập chữ thay vì số làm cin lỗi. Dùng cin.fail() để kiểm tra.

### Đường dẫn D:

Chỉ có trên Windows có ổ D. Ở nơi khác is_open() trả về false.

### Tham chiếu & con trỏ

&n cho phép hàm sửa n của main. a\[\] làm việc trực tiếp trên mảng gốc.

### Nhập

Truyền `int &n` để n trả về cho main.

### Mở file

Gọi `open()`, rồi kiểm tra `is_open()` trước khi ghi.

### Ghi file

Ghi n và xuống dòng, sau đó ghi từng phần tử kèm một dấu cách.

### Đóng file

Gọi `f.close()` để đẩy dữ liệu xuống đĩa.

← → / Space: chuyển · Shift+→: qua slide · Home: đầu · F: toàn màn hình

1/1