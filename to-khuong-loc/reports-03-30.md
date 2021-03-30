# Gitignore

## Gitignore là file có tên là .gitignore do Git quy định. Nhiệm vụ của nó là liệt kê những file mà mình không mong muốn cho vào git

## Các pattern format hay dùng

- Sử dụng # để comment, cách dòng
- Loại bỏ file: example.exe
- Loại bỏ thư mục: example_folder/
- Sử dụng 1 _ để tìm các file có cùng định dạng. Ví dụ như bạn muốn ignore tất cả các file .xml trong project: _.xml
- Trường hợp khác của 1 _ nếu bạn chỉ rõ đường dẫn ví dụ: config/_.xml thì nó chỉ có hiệu lực cho các file config/abc.xml mà không có hiệu lực cho các file config/sub/abc.xml.
- Sử dụng ** để có hiệu lực cho các thư mục không cần định rõ tên. Ví dụ: **/foo nó sẽ có hiệu lực cho tất cả file hoặc thư mục có tên là foo ở mọi nơi trong project.
- folder/\*\* : có hiệu lực cho tất cả các file bên trong thư mục.

## Ví dụ

    # Secret keys
    apikey

    # Dependency directories
    node_modules

## Lưu ý:

- Nếu tạo project có file .gitignore và liệt kê files, thư mục cần ignore ngay từ đầu thì không vấn đề gì

- Nếu file, folder đã đc push lên; sau đó clone về thì file đó đang thuộc quyên quản lý của git cache. Cần remove cache sau đó add, commit và push như bình thường:

      git rm -r --cached /path/to/file_or_folder
      hoặc
      git rm -r --cached .
