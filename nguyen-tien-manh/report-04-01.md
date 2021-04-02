# Nguyen Tien Manh - 04/01

## TOPIC: Git stash

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