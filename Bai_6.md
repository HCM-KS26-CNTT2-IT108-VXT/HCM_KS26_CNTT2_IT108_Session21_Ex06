# BÀI 6: ỨNG DỤNG AI TRONG KHẮC PHỤC LỖI GIT PERMISSION DENIED

*Sinh viên: Võ Xuân Thịnh – Lớp CNTT2-K26*

## 1. Tình huống của mình

Mình cần đẩy code lên GitHub cho kịp deadline thì Terminal báo lỗi:

```
error: open(".git/FETCH_HEAD"): Permission denied
```

Mình chạy lại vẫn bị. Cách xử lý của mình: nhờ AI giải thích lỗi, thử cách AI đưa, nếu vẫn không được thì báo cáo lỗi cho giảng viên.

## 2. Nhờ AI giải thích bằng Prompt 3 thành phần

Prompt gồm 3 phần: **Vai trò**, **Bối cảnh**, **Yêu cầu**.

```
[Vai trò] Bạn là một người hướng dẫn kiên nhẫn, giải thích cho sinh viên năm nhất chưa biết nhiều về Git.

[Bối cảnh] Tôi đang dùng Windows và đẩy code lên GitHub thì Terminal báo:
error: open(".git/FETCH_HEAD"): Permission denied
Tôi đã chạy lại lệnh nhưng vẫn bị lỗi.

[Yêu cầu] Hãy giải thích lỗi này bằng ngôn ngữ đời thường, có ví dụ so sánh dễ hiểu, không dùng thuật ngữ khó.
Sau đó đưa tối đa 3 cách xử lý an toàn, xếp từ dễ đến khó, và nói rõ rủi ro của từng cách.
```

**Vì sao prompt này tốt:** có vai trò nên AI giải thích đúng trình độ, có bối cảnh nên không trả lời lan man, có yêu cầu rõ nên câu trả lời ngắn và dùng được ngay.

**Giải thích bình dân (ý chính AI trả lời):**

- `Permission denied` = "bị từ chối quyền".
- Git cần mở file `.git/FETCH_HEAD` để ghi lại lần lấy dữ liệu, nhưng Windows **không cho tài khoản hiện tại ghi** vào file/thư mục đó.
- Giống như bạn có chìa khóa cổng nhà nhưng không có chìa phòng bên trong: vào được nhà mà không mở được phòng.
- Nguyên nhân hay gặp: thư mục `.git` thuộc quyền của người dùng khác hoặc ở chế độ chỉ đọc, file đang bị chương trình khác khóa, hoặc thư mục nằm ở nơi cần quyền cao hơn.

## 3. Thử chạy bằng quyền Administrator và chụp ảnh

**Các bước thực hiện (Windows):**

1. Đóng Terminal / Git Bash / VS Code đang mở.
2. Bấm phải vào **Git Bash** (hoặc Terminal), chọn **Run as administrator**, bấm **Yes**.
3. Dùng lệnh `cd` đi tới thư mục dự án, rồi chạy lại lệnh Git đã bị lỗi, ví dụ `git push`.
4. Chụp ảnh màn hình: một ảnh **trước** (lỗi cũ) và một ảnh **sau** (khi chạy bằng Administrator).

**Mẹo chụp ảnh chuyên nghiệp:**

- **Khoanh vùng lỗi** bằng khung đỏ hoặc mũi tên quanh dòng `Permission denied`.
- **Che thông tin cá nhân:** tên người dùng trong đường dẫn (`C:\Users\...`), email, token, mật khẩu.
- Chụp vừa đủ cửa sổ Terminal, thấy rõ lệnh đã gõ và kết quả. Không chụp cả màn hình lộn xộn.
- Đặt tên ảnh dễ hiểu, ví dụ `loi-truoc.png`, `chay-admin.png`.

**Ảnh minh họa (bạn tự chụp rồi thay vào đây):**

![Lỗi Permission denied trước khi chạy Administrator](loi-truoc.png)

![Kết quả sau khi chạy bằng Run as administrator](chay-admin.png)

**Lưu ý an toàn:** chỉ dùng quyền Administrator cho lệnh mình hiểu rõ. Chạy bằng quyền cao có thể tạo ra file thuộc quyền Administrator, về sau lại gây lỗi tương tự với tài khoản thường.

## 4. Nếu vẫn không sửa được: nhờ giảng viên theo Bug Reporting Framework

Một báo cáo lỗi tốt cần đủ: **Tiêu đề, Môi trường, Các bước tái hiện, Kết quả mong đợi, Kết quả thực tế, Đã thử, Ảnh đính kèm.**

**Tin nhắn gửi giảng viên:**

> **Tiêu đề:** [Hỗ trợ] Lỗi Git "Permission denied" ở `.git/FETCH_HEAD` khi push code, đã thử chạy Administrator vẫn lỗi
>
> Chào thầy/cô, em là Võ Xuân Thịnh, lớp CNTT2-K26. Em nhờ thầy/cô hỗ trợ lỗi Git dưới đây ạ.
>
> **1. Môi trường:**
> - Hệ điều hành: Windows [10/11]
> - Phiên bản Git: [chạy `git --version` rồi điền]
> - Công cụ đang dùng: [Git Bash / Terminal / VS Code]
> - Vị trí thư mục dự án: [ví dụ ổ D:, không phải thư mục hệ thống]
>
> **2. Các bước tái hiện:**
> 1. Mở Terminal tại thư mục dự án.
> 2. Chạy lệnh: `[lệnh em đã gõ, ví dụ git push]`
> 3. Terminal báo lỗi.
>
> **3. Kết quả mong đợi:** Code được đẩy lên GitHub thành công.
>
> **4. Kết quả thực tế:** Terminal báo `error: open(".git/FETCH_HEAD"): Permission denied`.
>
> **5. Em đã thử:**
> - Chạy lại lệnh nhiều lần: vẫn lỗi.
> - Mở Terminal bằng Run as administrator: [vẫn lỗi / lỗi khác].
> - Nhờ AI giải thích và làm theo hướng dẫn an toàn: chưa khắc phục được.
>
> **6. Ảnh đính kèm:** `loi-truoc.png`, `chay-admin.png` (đã che thông tin cá nhân).
>
> Em cần đẩy code trước hạn nộp **[ngày/giờ]**. Em cảm ơn thầy/cô ạ.

## 5. Tóm tắt 3 dòng (để thuyết trình)

- Lỗi `Permission denied` nghĩa là **Windows không cho tài khoản hiện tại ghi vào file `.git/FETCH_HEAD`**.
- Dùng **Prompt 3 thành phần** (Vai trò, Bối cảnh, Yêu cầu) để AI giải thích dễ hiểu, rồi thử **Run as administrator** và chụp ảnh có khoanh vùng, che thông tin cá nhân.
- Nếu vẫn lỗi, gửi **báo cáo lỗi đủ 7 phần** (tiêu đề, môi trường, các bước, mong đợi, thực tế, đã thử, ảnh) cho giảng viên.
