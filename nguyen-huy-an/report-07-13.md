# Nguyen Huy An - 07/13


## Gitignore

- Gitignore là file có tên là .gitignore do Git quy định. Nhiệm vụ của nó là liệt kê những file mà mình không mong muốn cho vào git

### Các pattern format hay dùng

- Sử dụng # để comment, cách dòng
- Loại bỏ file: example.exe
- Loại bỏ thư mục: example_folder/
- Sử dụng 1 _ để tìm các file có cùng định dạng. Ví dụ như bạn muốn ignore tất cả các file .xml trong project: _.xml
- Trường hợp khác của 1 _ nếu bạn chỉ rõ đường dẫn ví dụ: config/_.xml thì nó chỉ có hiệu lực cho các file config/abc.xml mà không có hiệu lực cho các file config/sub/abc.xml.
- Sử dụng ** để có hiệu lực cho các thư mục không cần định rõ tên. Ví dụ: **/foo nó sẽ có hiệu lực cho tất cả file hoặc thư mục có tên là foo ở mọi nơi trong project.
- folder/\*\* : có hiệu lực cho tất cả các file bên trong thư mục.

### Ví dụ

    # Secret keys
    apikey

    # Dependency directories
    node_modules

### Lưu ý:

- Nếu tạo project có file .gitignore và liệt kê files, thư mục cần ignore ngay từ đầu thì không vấn đề gì

- Nếu file, folder đã đc push lên; sau đó clone về thì file đó đang thuộc quyên quản lý của git cache. Cần remove cache sau đó add, commit và push như bình thường:

      git rm -r --cached /path/to/file_or_folder
      hoặc
      git rm -r --cached .


## Git stash

- Ví dụ khi đang code có khá nhiều file change mà phải qua branch khác fix bug, từ đây có 2 lựa chọn:
    - Chạy git reset --hard để loại bỏ những thay đổi đã được commit của bạn.
    - Ghi lại công việc chưa hoàn tất của bạn như là một commit mới.

    => Tùy chọn đầu tiên làm mất tất cả công việc của bạn, trong khi cái sau dẫn đến một phần commit không có ý nghĩa. Không có tình huống là được mong đợi cả.
- Git stash được sử dụng khi muốn lưu lại các thay đổi chưa commit, thường rất hữu dụng khi muốn đổi sang 1 branch khác mà lại đang làm dở ở branch hiện tại.

    ```sh
    git stash save
    ```

- Sau khi đã git stash 1 hoặc vài lần, có thể xem lại danh sách các lần lưu thay đổi bằng câu lệnh

    ```sh
    git stash list
    stash@{0}: WIP on <branch-name>: <lastest commit>
    stash@{1}: WIP on <branch-name>: <lastest commit>
    stash@{2}: WIP on <branch-name>: <lastest commit>
    ```

- Đôi khi muốn lấy lại thay đổi và xoá nội dung thay đổi lưu trong stack đi

    ```sh
    $ git stash apply stash@{1}
    $ git stash drop stash@{1}

- Hoặc đơn giản

    ```sh
    $ git stash pop stash@{1}
    ```

- Thậm chí nếu muốn xoá toàn bộ stack
    
    ```sh
    git stash clear
    ```

## Git Rebase

- Git Rebase là một chức năng được dùng khi gắn nhánh đã hoàn thành công việc vào nhánh gốc . Về mặt nội dung thì là việc điều chỉnh nhánh công việc gắn vào với nhánh gốc nên các commit sẽ được đăng kí theo thứ tự gắn vào . Chính vì thế sẽ có đặc trưng là dễ nhìn hơn sau khi xác nhận commit. Lí do chính sử dụng chính của Git Rebase đó là để lưu giữ lịch sử làm việc của dự án một cách tuyến tính. Ví dụ, hãy tưởng tưởng rằng bạn đang làm việc trên một branch riêng và cùng lúc đó, branch master có nhiều sự phát triển. Bạn muốn cập nhật branch của mình theo branch master, đồng thời lại muốn giữ lịch sử của branch mình không xê dịch để trông như thể bạn đã không bị ảnh hưởng bởi những cập nhật mới nhất này. Điều này sẽ giúp bạn merge nhánh phụ một cách gọn gàng hơn vào nhánh chính về sau. Ngoài ra, việc lưu trữ một lịch sử branch không bị thay đổi sẽ giúp các kỹ sư điều tra nguồn gốc của phân tích hồi quy trong những giai đoạn sau dễ dàng hơn.

- rebase cho phép phân tách, di chuyển hoặc thoát khỏi các commit. Nó cũng có thể được sử dụng để kết hợp hai nhánh khác nhau
