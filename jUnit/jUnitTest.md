# jUnit Test

## Các phương thức Assert()

Các phương thức assertXXX() được dùng để kiểm tra các điều kiện khác nhau.junit.framework.TestCase, lớp cha cho tất cả các test case, thừa kế từ lớp junit.framework.Assert. Lớp này định nghĩa khá nhiều các phương thức assertXXX(). Các phương thức test hoạt động bằng cách gọi những phương thức này.

Sau đây là mô tả các phương thức assertXXX() khác nhau có trong lớp junit.framework.Assert.

- `assertEquals()`: So sánh 2 giá trị để kiểm tra bằng nhau. Test sẽ được chấp nhận nếu các giá trị bằng nhau.
- `assertFalse()`: Đánh giá biểu thức luận lý. Test sẽ được chấp nhận nếu biểu thức sai.
- `assertNotNull()`: So sánh tham chiếu của một đối tượng với null. Test sẽ được chấp nhận nếu tham chiếu đối tượng khác null.
- `assertNotSame()`: So sánh địa chỉ vùng nhớ của 2 tham chiếu đối tượng bằng cách sử dụng toán tử ==. Test sẽ được chấp nhận nếu cả 2 đều tham chiếu đến các đối tượng khác nhau
- `assertNull()`: So sánh tham chiếu của một đối tượng với giá trị null. Test sẽ được chấp nhận nếu tham chiếu là null.
- `assertSame()`: So sánh địa chỉ vùng nhớ của 2 tham chiếu đối tượng bằng cách sử dụng toán tử ==. Test sẽ được chấp nhận nếu cả 2 đều tham chiếu đến cùng một đối tượng.
- `assertTrue()`: Đánh giá một biểu thức luận lý. Test sẽ được chấp nhận nếu biểu thức đúng fail(): Phương thức này làm cho test hiện hành thất bại, phương thức này thường được sử dụng khi xử lý các biệt lệ.

Mặc dù bạn có thể chỉ cần sử dụng phương thức `assertTrue()` cho gần như hầu hết các test, tuy nhiên thì việc sử dụng một trong các phương thức assertXXX() cụ thể sẽ làm cho các test của bạn dễ hiểu hơn và cung cấp các thông điệp thất bại rõ ràng hơn.

Tất cả các phương thức của bảng trên đều nhận vào một `String` không bắt buộc làm tham số đầu tiên. Khi được xác định, tham số này cung cấp một thông điệp mô tả test thất bại.

Ví dụ:
```java
    assertEquals(employeeA, employeeB);  
    assertEquals("Employees should be equal after the clone() operation.", employeeA, employeeB).
```
Phiên bản thứ 2 được ưa thích hơn vì nó mô tả tại sao test thất bại, điều này sẽ giúp cho việc sửa lỗi được dễ dàng hơn.
