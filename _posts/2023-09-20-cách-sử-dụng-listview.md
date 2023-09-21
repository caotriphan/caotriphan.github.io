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

Chọn Edit Columns

![Alt text](/assets/img/git-pics/edit columns lítview.png)

Chọn Add, khi đó bảng thuộc tính sẽ được hiện thị, chúng ta cần chú ý đến một số thuộc tính như: text - nhập header; TextAlign - left, right, hoặc center; Width - bề rộng cột mong muốn....

![Alt text](/assets/img/git-pics/adding columns listview.png)

Chúng ta cũng có thể thêm vào dữ liệu bằng cách edit Item.
        
![Alt text](/assets/img/git-pics/Edit Item ListView.png)

Chọn Add để thêm vào Item, sau đó bên bảng thuộc tính, chúng ta sẽ nhập dữ liệu vào ô đầu tiên ứng với cột đầu tiên của header. Chúng ta chọn SubItem để thêm vào thông tin các cột tiếp theo.

![Alt text](/assets/img/git-pics/adding items listview.png)

Ở phần thuộc tính Text chúng ta nhập tiếp thông tin thứ 2 ứng với cột header. 

![Alt text](/assets/img/git-pics/adding more info item listview.png)

##### 2- Sử dụng ListView Class để tạo điều khiển ListView.

- Dựa trên việc tạo điều khiển List View bằng List View class, chúng ta cũng có thể dễ dàng show chi tiết các thuộc tính của List View bằng các dòng code:

     + Hiển thị chi tiết
     + Cho phép người dùng chỉnh sửa thuộc tính Text của Item
     + Sắp xếp lại các cột.
     + Hiển thị check boxes.
     + Hiển thị đường lưới.
     + Sắp xếp thứ tự của các Item theo thư stuwj tăng dần.
     + vvv....

- Tạo Item và các SubItem của các Item.
- Tạo các cột cho Item và SubItem.
- Điều khiển bề rộng của các cột.
- Thêm các Item vào List View.
- Chúng ta cũng có thể thêm hình ảnh vào trong List View bằng cách tạo đối tượng hình ảnh.
- Và cuối cùng là thêm ListView vào bộ sưu tập điều khiển.

- Dưới đây là ví dụ của việc tạo và điều khiển ListView bằng ListView Class:

<script src="https://gist.github.com/caotriphan/293227433b7726ab988e080ef6af82ac.js"></script>

#### Một số thuộc tính đáng chú ý của ListView

Chúng ta hãy cùng xem lại một số thuộc tính thường dùng tiêu biểu của ListView:

- View: Thuộc tính này quy định cách hiển thị của các Item trong ListView, bao gồm 5 giá trị: Detail, Largelcons, list, Smallcons, Titles.
![Alt text](/assets/img/git-pics/View in listview.png)

- Multiselect: Cho phép hoặc không cho phép chọn một lúc nhiều Item trong ListView
![Alt text](/assets/img/git-pics/multiselect listview.png)

- FullRowSelect: khi chọn dòng dữ liệu highlighted cả dòng hay chỉ ô được chọn.

- GridLines: cho phép có hoặc không hiển thị các dòng và cột dạng lưới.

- SelectedItems: trả về tập các Item được chọn trong Listview.

- LargerImageIcon/SmallImageIcon : gán đối tượng ImageList cho ListView.

- Selectedindices: Trả về danh sách chỉ mục được chọn.

- Items: Trả về các Items chứa trong ListView.

#### Một số phương thức thường dùng của ListView:

- Clear(): Xóa tất cả các Item và Column trong Listview.

- Sort(): Sắp xếp các Item trong ListView.

- GetItemAt(x, y): Lấy Item tại vị trí tọa độ x và y.

#### Một số sự kiện thường dùng của ListView:

- SelectedIndexChanged: Sự kiện phát sinh khi có sự thay đổi về chỉ mục được chọn của Item trên ListView.

- ItemSelectionChanged: Sự kiện phát sinh khi có sự thay đổi lựa chọn một Item trên ListView.

- ItemCheck: Xảy ra khi trạng thái chọn của Item thay đổi.

- ColumnClick: Sự kiện phát sinh khi có sự thay đổi lựa chọn một Item trên ListView.

- MouseClick: Sự kiện phát sinh khi nhấp chuột chọn Item trong ListView.

### Summary

Trong bài viết này, chúng ta đã nói về cách tạo điều khiển ListView trong Windows Forms. Sau đó, chúng ta đã biết cách sử dụng các thuộc tính và phương thức khác nhau. Cùng chờ đón nhiều bài viết về các chủ đề khác thú vị hơn nhé.