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
    
    ![rebase-01](https://user-images.githubusercontent.com/41434223/112982066-3a9dd700-9186-11eb-88f1-58f160d5b321.PNG)

    - Nhấn i để edit content, trừ commit trên cùng, sửa command của 2 commit sau từ pick thành squash

    ![rebase-02](https://user-images.githubusercontent.com/41434223/112982134-51442e00-9186-11eb-966f-4e7c9492b049.PNG)

    - Ấn ESC => : => w => r, hiển thị giao diện tổng hợp lại 3 commit để chọn hoặc sửa để thay thế mới

    ![rebase-03](https://user-images.githubusercontent.com/41434223/112982161-5a34ff80-9186-11eb-847d-0867041d1b28.PNG)

    - Có thể dùng # để bỏ message và rename message

    ![rebase-04](https://user-images.githubusercontent.com/41434223/112982179-5f924a00-9186-11eb-849a-ab3cd846c662.PNG)

    - Sau đó ấn ESC => : => w => r

