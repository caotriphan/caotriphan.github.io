---
title: Làm quen với Json Serialization trong C#
author: Lucas Phan
description: Làm quen với Json Serialization trong C#
---

### Mở đầu

Đối với các ứng dụng nói chung và viết bằng C# nói riêng thì làm việc với Json là một trong những công việc thường xuyên. Trong bài viết này mình sẽ tổng hợp một số kiến thức khi làm việc với Json C#.

### Nhắc lại về JSON

Json (JavaScript Object Notation) là định dạng dữ liệu phổ biến trong lập trình. Json sử dụng các ký tự để biểu thị kiểu dữ liệu. Ví dụ:

**Object**: Json Object với hai property

```json
{ "id": 1, "name": "John" }
```

**Array**

```json
[1,2,3] // number array
[{ "id": 1, "name": "John" }] // object array
```

Về cơ bản Json giống với JavaScript Object, sự khác biệt là các property của Json phải nằm trong dấu `""`.

### C# Serialization

Một trong những thư viện phổ biến để làm việc với Json đó là NewtonSoft.Json. Kể từ khi .NET Core support built-in Json, chúng ta có thêm sự lựa chọn để làm việc với Json. Hai thư viện này có cách sử dụng gần giống như nhau. Vì thư viện built-in ngày càng được tập trung phát triển, cho nên trong bài biết này mình sẽ tập trung nói về thư viện built-in, cụ thể là System.Text.Json.

### Serialization

Serialization là quá trình đổi từ Object thành Json mà cụ thể là Json String. Bằng cách sử dụng method: `System.Text.Json.JsonSerializer.Serialize();`

Ví dụ:

<script src="https://gist.github.com/caotriphan/b70bb2a280f99ded0eed18f16a068725.js"></script>

Ví dụ trên là một ví dụ đơn giản trong việc Serialize một Object thành dạng Json String và hầu như không có nhiều điều để nói về quá trình Serialization này. 

### Deserialization

Deserialization là quá trình ngược lại so với serialization, chuyển đổi từ Json String sang Object. Bảng cách sử dụng method: `System.Text.Json.JsonSerializer.Deserialize();`

Ví dụ: 

<script src="https://gist.github.com/caotriphan/5314aab90e8a87b6927f7b38f9a9ba30.js"></script>

Deserialize cũng khá đơn giản và tương đồng với Serialize. Tuy nhiên, ta có một vài lưu ý: 

#### Column mapping:

Mặc định khi Deserialize thì Json Property cần phải giống với Object Property. Cụ thể, nếu như ta có Json như sau:

```json
{"FirstName": "John"}
```

thì có thể convert thành một object với property là `FirstName`: 

```cs
class Person 
{
    public string FirstName { get; set; }
}
```

cho nên nếu Json property mà khác với object property thì chúng ta cần phải dùng custom mapping bằng cách sử dụng attribute `JsonPropertyName`

![Alt text](/assets/img/json-csharp/column-mapping.png)

### Lí do nên sử dụng Serialization/Deserialization trong C#

Serialization rất hữu ích cho việc lưu trữ và trao đổi trạng thái đối tượng. Trong bộ nhớ ứng dụng, trạng thái của một đối tượng nằm trong các cấu trúc dữ liệu phức tạp không phù hợp để lưu trữ hoặc trao đổi qua mạng.

Vì vậy, Serialization sẽ chuyển đổi đối tượng thành định dạng có thể chia sẻ được. Với Serialization chúng ta có thể chuyển đổi các đối tượng:
 - Giữa máy khách và máy chủ thông qua RESTful API hoặc gRPC.
 - Qua mạng dành cho các hệ thống nhắn tin.
 - Thông qua tường lửa dưới dạng chuỗi như JSON hoặc XML.
 - Đến các kho dữ liệu khác nhau như cơ sở dữ liệu SQL hoặc NoSQL để lưu trữ lâu dài.

 Deserialization thì thường hữu ích trong việc tái cấu trúc đối tượng về trạng thái ban đầu tại đích để tiếp tục xử lý.

 Trên đây là các lý do tại sao chúng ta nên sử dụng Serialization và Deserialization. Vậy câu hỏi được đặt ra là rốt cuộc Serialization và Deserialization là gì? Chúng ta hãy cùng nhau tìm hiểu nhé.


### Hỗ trợ Serialization/Deserialization trong C# và .NET framework

Dữ liệu JSON là định dạng phổ biến ngày nay khi truyền dữ liệu giữa các ứng dựng. Khi xây dựng một ứng dụng .NET, việc chuyển đổi định dạng dữ liệu JSON sang đối tượng .NET và ngược lại là rất phổ biến.

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
