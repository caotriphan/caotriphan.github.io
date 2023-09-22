---
title: Cách sử dụng Serialize và Deserialize trong C#
author: Lucas Phan
description: Cách sử dụng Serialize và Deserialize trong C#
---

### Mở Đầu

Serialization rất hữu ích cho việc lưu trữ và trao đổi trạng thái đối tượng. Trong bộ nhớ ứng dụng, trạng thái của một đối tượng nằm trong các cấu trúc dữ liệu phức tạp không phù hợp để lưu trữ hoặc trao đổi qua mạng.

Vì vậy, Serialization sẽ chuyển đổi đối tượng thành định dạng có thể chia sẻ được. Với Serialization chúng ta có thể chuyển đổi các đối tượng:
 - Giữa máy khách và máy chủ thông qua RESTful API hoặc gRPC.
 - Qua mạng dành cho các hệ thống nhắn tin.
 - Thông qua tường lửa dưới dạng chuỗi như JSON hoặc XML.
 - Đến các kho dữ liệu khác nhau như cơ sở dữ liệu SQL hoặc NoSQL để lưu trữ lâu dài.

 Deserialization thì thường hữu ích trong việc tái cấu trúc đối tượng về trạng thái ban đầu tại đích để tiếp tục xử lý.

 Trên đây là các lý do tại sao chúng ta nên sử dụng Serialization và Deserialization. Vậy câu hỏi được đặt ra là rốt cuộc Serialization và Deserialization là gì? Chúng ta hãy cùng nhau tìm hiểu nhé.

 ### Định nghĩa Serialization và Deserialization trong C#?

 #### Serialization

 Serialization là quá trình để chuyển đổi một cấu trúc dữ liệu hoặc đối tượng thành một định dạng có thể lưu trữ được (Ví dụ trên file, trên cơ sở dữ liệu, hoặc trên bộ nhớ), hoặc có thể truyền được qua mạng.

 Cũng có thể coi Serialization là tiền đề cho quá trình lưu trữ trạng thái của một Object trong một môi trường trung gian để có thể khôi phục lại khi cần thiết.

 Serialization thực tế có thể chuyển đổi Object về mảng Byte (Binary Serialization), hoặc về chuối văn bản (Text Serialization). Tuy nhiên, việc chuyển đổi này không thể tùy tiện mà phải đảm bảo thực hiện được việc giải mã để khôi phục lại Object từ dạng trung gian.


 #### Deserialization

 Quá trình khôi phục lại Object từ dạng trung gian được gọi là giải trình tự hóa (Deserilization.)


### Hỗ trợ Serialization và Deserialization trong C3 và .NET Frameword
 
### Summary
