# Nguyen Tien Manh - 03/30

## TOPIC: Sử dụng rebase commit message git

- Khi code mà thực hiện commit nhiều lần với cùng 1 vấn đề. Thay vì sử dụng lại comment trước đó thì bạn có thể tận dụng lại commit trước đó. Hoặc thực hiện gộp nhiều commit lại.

- Để tận dụng lại commit trước, thêm tham số –amend vào lệnh git commit như sau

    ```sh
    git commit --amend
    ```

- Có thể thay đổi lại message của commit trước

    ```sh
    git commit --amend -m 'Nội dung thay đổi'
    ```
- Gộp nhiều commit thành một: ví dụ gộp 3 commit

    ```sh
    git rebase -i HEAD~3
    ```

    - Layout sẽ hiển thị
    
    ![title](images/rebase-01.png)
    
    - Nhấn i để edit content, trừ commit trên cùng, sửa command của 2 commit sau từ pick thành squash

    ![title](images/rebase-02.png)

    - Ấn ESC => : => w => r, hiển thị giao diện tổng hợp lại 3 commit để chọn hoặc sửa để thay thế mới

    ![title](images/rebase-03.png)

    - Có thể dùng # để bỏ message và rename message

    ![title](images/rebase-04.png)

    - Sau đó ấn ESC => : => w => r

