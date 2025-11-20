# LÝ THUYẾT VÀ ỨNG DỤNG CỦA LOGIC MỆNH ĐỀ

**Mô tả ngắn gọn về dự án:** Công cụ lập trình này được phát triển bằng C++ để giải quyết các bài toán về Logic Mệnh đề (Propositional Logic). Nó cung cấp khả năng tự động xây dựng bảng chân trị cho các biểu thức logic và đánh giá xem biểu thức đó là Hằng đúng, Mâu thuẫn, hay Ngẫu nhiên.


## 👥 Danh sách Thành viên
| Tên Sinh Viên | Mã Sinh Viên |
| :--- | :--- |
| Nguyễn Khắc Thịnh | B24DCCN545 |
| Ngô Minh Đức | B24DCCN138 |
| Đinh Quý Quang | B24DCCN469 |
| Mai Văn Mạnh | B24DCCN381 |


---
## 🛠️ Hướng dẫn Cài đặt & Chạy chương trình
Dự án này được viết bằng C++ và sử dụng các thư viện chuẩn. Bạn cần có một trình biên dịch C++ (ví dụ: GCC, Clang) đã được cài đặt trong hệ thống.

### 1. Yêu cầu Hệ thống

* **Hệ điều hành:** Windows, macOS, hoặc Linux.
* **Trình biên dịch:** GCC/G++ (phiên bản 7.0 trở lên) hoặc tương đương.

### 2. Cài đặt

Không cần cài đặt thư viện bên ngoài. Mã nguồn chỉ sử dụng `<bits/stdc++.h>` (hoặc các thư viện chuẩn C++ tương đương như `<iostream>`, `<string>`, `<map>`, `<vector>`).

### 3. Hướng dẫn Compile và Chạy

Thực hiện các bước sau trong Terminal (Command Prompt/Bash):

1.  **Lưu mã nguồn:** Đảm bảo file mã nguồn (ví dụ: `logic_solver.cpp`) nằm trong thư mục làm việc hiện tại.
2.  **Compile (Biên dịch):**
    ```bash
    g++ logic_solver.cpp -o logic_solver -std=c++17
    ```
    *Lưu ý: Bạn có thể thay `-std=c++17` bằng phiên bản chuẩn C++ khác tùy thuộc vào mã nguồn.*
3.  **Chạy chương trình:**
    * **Linux/macOS:**
        ```bash
        ./logic_solver
        ```
    * **Windows:**
        ```bash
        logic_solver.exe
        ```
4.  **Tương tác:** Chương trình sẽ yêu cầu bạn **nhập số lượng biểu thức** cần thực hiện, sau đó là **từng biểu thức logic** (ví dụ: `(P AND Q) IMPLIES R`).

---

## 📜 Quy tắc Nhập Biểu thức Logic

Để chương trình hoạt động chính xác, người dùng cần **TUÂN THỦ NGHIÊM NGẶT** các quy tắc nhập liệu sau:

1.  **Số lượng Biểu thức:**
    * **BƯỚC ĐẦU TIÊN** là nhập **số lượng biểu thức** (một số nguyên dương) mà bạn muốn đánh giá.

2.  **Định dạng Toán tử:**
    * **BẮT BUỘC** phải nhập **TÊN CÁC PHÉP TOÁN BẰNG CHỮ HOA** (in hoa) và có khoảng trắng ở hai bên toán tử.
    * *Ví dụ:* Sử dụng `P AND Q`, không dùng `P and Q` hay `PANDQ`.

3.  **Thứ tự Ưu tiên khi nhập:**
    * Chương trình xử lý các phép toán theo mức độ ưu tiên sau (nếu không có ngoặc `()`):
        | Ưu tiên | Phép toán |
        | :---: | :--- |
| **1 (Cao nhất)** | **NOT** (Phủ định) |
        | **2** | **AND** (Hội) |
        | **3** | **OR** / **XOR** (Tuyển / Tuyển loại) |
        | **4** | **IMPLIES** (Kéo theo) |
        | **5 (Thấp nhất)** | **EQUIVALENT** (Tương đương) |

4.  **Sử dụng Ngoặc `()` (Bắt buộc cho NOT):**
    * **Phép toán `NOT`:** Bất kỳ biến hoặc biểu thức nào bị phủ định bởi **NOT** phải được đặt trong **dấu ngoặc đơn** `()`.
        * **Đúng:** `(NOT P)`, `Q OR (NOT R)`
        * **Sai:** `NOT P`
    * **Thay đổi Ưu tiên:** Dấu ngoặc đơn có thể được sử dụng để ghi đè thứ tự ưu tiên mặc định. Biểu thức trong ngoặc sẽ được tính toán trước.
  
---
## ✨ Các Tính năng Chính

Công cụ này được thiết kế để xử lý các biểu thức logic mệnh đề và cung cấp kết quả chi tiết:

1.  **Hỗ trợ đa dạng Toán tử:** Xử lý các phép toán logic cơ bản sau:
    * **NOT** (Phủ định)
    * **AND** (Hội)
    * **OR** (Tuyển)
    * **XOR** (Tuyển loại)
    * **IMPLIES** (Kéo theo)
    * **EQUIVALENT** (Tương đương)
3.  **Đánh giá Độ ưu tiên:** Tuân thủ đúng thứ tự ưu tiên của các phép toán logic, bao gồm cả việc xử lý **ngoặc đơn `()`** lồng nhau.
4.  **Xây dựng Bảng Chân trị:** Tự động tạo và hiển thị **bảng chân trị** đầy đủ cho biểu thức, liệt kê tất cả $2^n$ trường hợp (với $n$ là số lượng biến).
5.  **Phân loại Biểu thức:** Đánh giá và xác định loại của biểu thức sau khi xây dựng bảng chân trị:
    * **Tautology (Hằng đúng)**: Nếu tất cả các kết quả là **T**.
    * **Contradiction (Mâu thuẫn)**: Nếu tất cả các kết quả là **F**.
---

## 📝 Ví dụ Mẫu

Dưới đây là các ví dụ minh họa cách chương trình hoạt động và kết quả đầu ra:

### Ví dụ 1: Ưu tiên AND trước OR (Tự động)

* **Biểu thức nhập:** `a OR b AND c`
* **Diễn giải:** Chương trình tự động hiểu biểu thức là $\mathbf{a \lor (b \land c)}$ do **AND** có độ ưu tiên cao hơn **OR**.
- Nhap so bieu thuc can thuc hien: 1
- Nhap bieu thuc thu 1 : W = a OR b AND c
- Bang chan tri:
---------------------------
a b c W  
T T T T  
T T F T  
T F T T  
T F F T  
F T T T  
F T F F  
F F T F  
F F F F  
=> Contingency!


### Ví dụ 2: Sử dụng NOT và XOR

* **Biểu thức nhập:** `(NOT p) AND q XOR (NOT r)`
* **Lưu ý:** Biểu thức này tuân thủ quy tắc ngoặc cho NOT.

- Nhap so bieu thuc can thuc hien: 1
- Nhap bieu thuc thu 1 : W = a OR b AND c
- Bang chan tri:

---------------------------------------  
a b c W  
T T T T  
T T F T  
T F T T  
T F F T  
F T T T  
F T F F  
F F T F  
F F F F  
=> Contingency!
Beta
0 / 10
used queries
1
