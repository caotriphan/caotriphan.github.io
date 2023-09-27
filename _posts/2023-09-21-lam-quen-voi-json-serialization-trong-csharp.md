---
title: Làm quen với Json Serialization trong C#
author: Lucas Phan
description: Làm quen với Json Serialization trong C#
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


### Hỗ trợ Serialization/Deserialization trong C# và .NET framework

<!-- Việc chuyển một Object về chuỗi ký tự hoặc mảng byte là một công việc tương đối phức tạp, tốn công sức và dễ sai sót, đặc biệt là đối với các class lớn có nhiều trường dữ liệu cũng như khi phải làm việc với nhiều class khác nhau.

Để hỗ trợ cho người lập trình, .NET framework cung cấp các class hỗ trợ cho 3 loại Serialization: Binary, XML, và JSON. -->

<!-- #### BinaryFormatter

**BinaryFormatter** class: biến đổi Object về mảng byte và ghi trực tiếp vào một stream; đọc các byte dữ liệu từ một stream và biến đổi về object. Lớp BinaryFormatter nằm trong không gian trên System>runtime.Serialization.Formatters.Binary.

##### Xây dựng cấu trúc Solution:

- Tạo mới một Solution trống đặt tên là ....
- Tạo mới 3 project trong solution này: Client (Console App), Server (Console App), Common (Class Library(>NET framework)).
- Thiết lập Multiple startup projects cho Client và Server
- Thêm 2 file mã nguồn Student.cs và TextSerializer.cs vào Common.
- Thiết lập cho Client tham chiếu tới thư viện Common. -->

Dữ liệu JSON là định dạng phổ biến ngày nay khi truyền dữ liệu giữa các ứng dựng. Khi xây dựng một ứng dụng .NET, việc chuyển đổi định dạng dữ liệu JSON sang đối tượng .NET và ngược lại là rất phổ biến.

Serialization là quá trình chuyển đổi các đối tượng .NET, chẳng hạn như chuỗi, thành định dạng JSON. Và Deserialization là quá trình chuyển đổi dữ liệu JSON thành các đối tượng .NET. Chúng ta hãy cùng nhau tìm hiểu Serialization và Deseialization JSON trong c# nhé.

Trước tiên, câu hỏi được đặt ra là vậy JSON là gì?

JSON (JavaScript Object Notation) là kiểu định dạng dữu liệu tuân theo một quy luật nhất định mà hầu hết các ngôn ngữ lập trình hiện nay có thể đọc được.JSON là một tiêu chuẩn mở để trao đổi dữ liệu trê web.

JSON hỗ trợ hai cấu trúc dữ liệu sau:
 - Tập hợp các cặp tên/giá trị - Các ngôn ngữ lập trình khác nhau hỗ trợ Cấu Trức Dữ Liệu này.
 - Danh sách các giá trị được sắp xếp - bao gồm một mảng, danh sách, vector hoặc chuối,...

 Chúng ta có thể triển khai Serialization/Deserialization theo 3 cách sau:

 - Sử dụng JavaScriptSerializer class
 - Sử dụng DataContractJsonSerializer class
 - Sử dụng JSON.NET library
 - Sủ dụng Built-in System.Text.Json

 Chúng ta hãy cùng nhay tìm hiểu cách sử dụng JSON.NET library cụ thể là NewtonSoft.Json và sử dụng Built-in System.Text.Json nhé, cũng là cách chúng ta thường hay dùng nhất:

 ### Using Json.NET

 Json.NET là thư viện của bên thứ 3 giúp chuyển đổi giữa văn bản JSON và các đối tượng .NET bằng cách sử dụng JsonSerializeer. JsonSerializer chuyển đổi các đối tượng .NET thành văn bản tương đương JSON và ngược lại bằng cách mapping tên thuộc tính đối tượng .NET thành tên thuộc tính JSON.

 Chúng ta hãy bắt đầu bằng việc cài đặt và triển khai nhé:

 - Trong Visual Studio, đi tới Tools Menu -> chọn Library Package Manager -> Package  Manager Console. Một cửa sổ lệnh nơi chúng ta đặt lệnh được mở ra, nơi mà chúng ta cài đặt Newtonsoft.Json. 

 **Hoặc**

 - Trong Visual Studio, Tools menu -> Manage Nuget Package Manager Solution and type "JSON.NET" để tìm kiếm nó online.

![Alt text](/assets/img/git-pics/installing-json.NET.png)

<script src="https://gist.github.com/caotriphan/8f3a1ca7a78ecfa8c6862dc8f69b0799.js"></script>

### Using System.Text.Json

<script src="https://gist.github.com/caotriphan/ca875fabfea944f49a08615b75397af9.js"></script>

- Khởi tạo class Employee có các properties là Id, Name, Address.
- Tiếp theo, tạo một đối tượng để mở/tạo tệp "JSONSerializationExample", chỉ định giá trị cho ID, Name, và Address.
- Tạo đường dẫn lưu trữ file
- Serialize, ghi file, đọc file cho ra kết quả là một file Json.
### Summary

Bài viết này giới thiệu kỹ thuật "Serialization và Deserialization". Các bươc thực hiện được giải thích rõ ràng và đầy đủ để các bạn dễ hiểu. Những kỷ thuật này được sử dung khá thường xuyên khi phát triển cac sứng dụng giao tiếp qua mạng. Serialization là quá trình chuyển đổi một đối tượng thành một biểu mẫu để nó có thể được lưu trữ trong tệp, cơ sở dữ liệu hoặc bộ nhớ; hoặc được chuyển qua mạng. Mục đích chính của nó là lưu trạng thái của một đối tượng để có thể tạo lại khi cần thiết. Deserialization thì ngược lại với Serialization. 
Hy vọng mọi người thấy bài viết này thú vị. 
