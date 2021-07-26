# report-app

## Nội dung phải đọc: `git policy`
https://github.com/vmodev11/vmo11/blob/master/documents/GIT_POLICY.md

## Nội dung phải đọc: `coding conventions`
https://github.com/vmodev11/vmo11/blob/master/documents/JAVASCRIPT_STYLE_GUIDE.md

## NẾU THÀNH VIÊN NÀO LÀM MẤT REPORT (MẤT CODE) CỦA CÁC THÀNH VIÊN CÒN LẠI THÌ PHẢI CÓ TRÁCH NHIỆM BÁO LẠI VÀ ĐI SỬA LẠI CHO NGƯỜI BỊ MẤT CODE. ĐIỂM ĐÁNH GIÁ CŨNG SẼ DỰA TRÊN YẾU TỐ NÀY

## Hướng dẫn làm việc với `REPORT-APP`:
- Clone project và tạo branch của mình theo rule được mô tả trong git policy ở trên
- Yêu cầu cấu hình và sử dụng SSH
- File `reports.md` là file report chung đầu ngày của tất cả mọi người
- Mỗi người sẽ sẽ tạo 1 folder theo tên của mình và tạo các file md để report cuối ngày theo mẫu
```
- nguyen-van-a
--- report-03-26.md
--- report-03-27.md
```
- Lưu ý về cách viết commit có trong phần git policy ở trên
- Bắt đầu ngày làm việc mọi người thực hiện report vào file `reports.md`, commit và push lên nhánh của mình, sau đó tạo Pull Request trên github vào nhánh `main`. Nếu không thấy có conflict thì mọi người có thể tiến hành merge. Nếu xảy ra conflict thì có nhiều cách để xử lý nhưng chúng ta sẽ chọn cách `rebase` theo các bước sau
1. Kiểm tra sự thay đổi trên nhanh `main`
2. Trên nhánh hiện tại `rebase` nhánh `main` để lấy về các thay đổi mới nhất
3. Kiểm tra các thay đổi trên nhanh hiện tại, nếu không có vấn đề gì thì tiến hành `push` với cờ --force để ghi đè lịch sử git của nhánh hiện tại
4. Kiểm tra lại PR hiện tại và tiền hành merge.

*Hint: PR của người đầu tiên sẽ không bị conflict*

- Cuối ngày mọi người thực hiện report tương tự như trên. Lưu ý các report cuối ngày có thể kèm theo các ví dụ về code nên hãy viết chúng với md như thế này:
```javascript
function demo() {
  ...
}
```
- Yêu cầu: Với cách sử dụng `rebase` sẽ không có phát sinh các commit thừa 1 cách vô nghĩa.
- **Có thể tự tạo các repository tương tự để thực hành**

## Chúc mọi người không sợ GIT
