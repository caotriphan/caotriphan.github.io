---
title: Cách sử dụng List View trong C#
author: Lucas Phan
description: Cách sử dụng List View trong C#
---

### C# ListView

Trong C# ListView cung cấp giao diện để hiển thị danh sách các mục bằng các chế độ xem khác nhau bao gồm văn bản và hình ảnh. Trong hướng dẫn này, chúng ta sẽ tìm hiểu cách tạo và sử dụng điều khiển listview trong c#. Bài viết này cũng đề cập đến hầu hết các thuộc tính và phương thức phổ biến của điều khiển List View.

#### Cách tạo List View trong C#

List View được tạo ra trong windows form trong C#. Chúng ta có hai phương pháp để tạo ra điều khiển List View:

- Với toolbox bên phía trái màn hình, chúng ta kéo và thả điều khiển List View từ trong toolbox vào form.

     ![Alt text](/assets/img/git-pics/create listview.png)

- Mối đối tượng hiển thị trong LstView được gọi là Item. Item được tạo ra từ ListViewItem. Mỗi Item có thuộc tính Text là chỗi kí tự hiển thị ở cột đầu tiên trong ListView, mỗi Item có các SubItem hiện thị ở các cột tiếp theo trong ListView.

##### 1- Sử dụng Designer Forms để tạo điều khiển tại thời điểm thiết kế.
![Alt text](/assets/img/git-pics/edit columns lítview.png)

![Alt text](/assets/img/git-pics/adding columns listview.png)
        
![Alt text](/assets/img/git-pics/Edit Item ListView.png)


##### 2- Sử dụng ListView Class để tạo điều khiển lúc runtime.

### Summary

Trong bài viết này, chúng ta đã nói về cách tạo điều khiển ListView trong Windows Forms. Sau đó, chúng ta đã biết cách sử dụng các thuộc tính và phương thức khác nhau. Cùng chờ đón nhiều bài viết về các chủ đề khác thú vị hơn nhé.