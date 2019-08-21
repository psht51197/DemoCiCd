# Build Script

1.  Tổng quan :

    - App center cho phép người dùng custom buildscrip, những script này sẽ được chạy tuỳ vào giai đoạn.
    - App center cung cấp cho người dùng 3 giai đoạn để có thể custom:
    - [`Post - clone`](https://docs.microsoft.com/en-us/appcenter/build/custom/scripts/#post-clone) : thực hiện **sau** khi clone project
    - [`Pre - build`](https://docs.microsoft.com/en-us/appcenter/build/custom/scripts/#pre-build) : thực hiện **trước** khi bắt đầu build
    - [`Post - build`](https://docs.microsoft.com/en-us/appcenter/build/custom/scripts/#post-build) : thực hiện **sau** khi build

2.  Ví dụ :
    - sử dụng Pre - Build để thực hiện `npx jetify` để fix lỗi sai thư viện trên android
      - tạo file `appcenter-pre-build.sh` tại thư mục gốc,
        với nội dung :


        ```python
        #!/bin/bash
        npx jetify
        ```

## - **Lưu ý :**

> nhập đúng tên file , vi appcenter dựa vào tên file để có thể nhận biết giai đoạn thực hiện
