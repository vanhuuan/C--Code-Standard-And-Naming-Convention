# Tiêu chuẩn coding và cách đặt tên trong C#


| Loại dữ liệu              | Cách Viết    | Độ dài | Số nhiều | Tiền tố| Hậu tố | Viết tắt     | Kí tự hợp lệ       | Chưa dấu gạch dưới|
|:--------------------------|:-------------|-------:|:---------|:-------|:-------|:-------------|:-------------------|:------------------|
| Tên Namespace             | PascalCasing |    128 | Có       | Có     | Không  | Không        | [A-z][0-9]         | Không             |
| Tên Lớp                   | PascalCasing |    128 | Không    | Không  | Có     | Không        | [A-z][0-9]         | Không             |
| Tên Hàm dựng              | PascalCasing |    128 | Không    | Không  | Có     | Không        | [A-z][0-9]         | Không             |
| Tên Hàm                   | PascalCasing |    128 | Có       | Không  | Không  | Không        | [A-z][0-9]         | Không             |
| Tên Tham Số Hàm           | camelCasing  |    128 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Không             |
| Tên Biến Cục Bộ           | camelCasing  |     50 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Không             |
| Tên Hằng                  | PascalCasing |     50 | Không    | Không  | Không  | Không        | [A-z][0-9]         | Không             |
| Tên Trường                | camelCasing  |     50 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Có                |
| Tên Thuộc tính            | PascalCasing |     50 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Không             |
| Tên Delegate              | PascalCasing |    128 | Không    | Không  | Có     | Có           | [A-z]              | Không             |
| Tên Kiểu Enum             | PascalCasing |    128 | Có       | Không  | Không  | Không        | [A-z]              | Không             |

#### 1. Sử dụng cách Viết Hoa Các Chữ Cái Đầu (PascalCasing) để đặt tên cho lớp và hàm:

```csharp
public class ClientActivity
{
  public void ClearStatistics()
  {
    //...
  }
  public void CalculateStatistics()
  {
    //...
  }
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework and và dễ đọc hiểu code.***

#### 2. Sử dụng cách viết Thường Chữ Cái Đầu Tiên (camelCasing) để đặt tên cho tên thuộc tính và tên tham số hàm:

```csharp
public class UserLog
{
  public void Add(LogEvent logEvent)
  {
    int itemCount = logEvent.Items.Count;
    // ...
  }
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework and và dễ đọc hiểu code.***

#### 3. Không được sử dụng cách đặt tên theo kiểu Hungarian hay bất kì các loại khác cho khai báo biến:

```csharp
// Cách đặt tên đúng
int counter;
string name;    
// Cách đặt tên cần phải tránh
int iCounter;
string strName;
```

***Lí do: Thống nhất chung với cách đặt tên của Microsoft's .NET Framework và Visual Studio IDE nhằm xác định kiểu dữ liệu dễ dàng hơn ( sử dụng công cụ của IDE).Tóm lại, bạn cần tránh đặt tên biến kèm theo kiểu dữ liệu của biến.***

#### 4. Không viết hoa tất cả các kí tự của hằng và biến readonly (chỉ đọc):

```csharp
// Cách đặt tên đúng 
public const string ShippingType = "DropShip";
// Cách đặt tên cần phải tránh
public const string SHIPPINGTYPE = "DropShip";
```

***Lí do: Thống nhất với cách đặt tênc của Microsoft's .NET Framework. Viết hoa thu hút nhiều sự chú ý không cần thiết.***

#### 5. Đặt tên một cách có ý nghĩa cho tên biến. Ví dụ sau đây sử dụng biến seattleCustomers cho các customers sống ở Seattle:

```csharp
var seattleCustomers = from customer in customers
  where customer.City == "Seattle" 
  select customer.Name;
```

***Why: Thống nhất với cách đặt tên của Microsoft's .NET Framework and và dễ đọc hiểu code.***

#### 6. Tránh sử dụng từ viết tắt. Ngoại lệ: Các từ viết tắt thường được sử dụng cho các tên thông dụng, như là Id, Xml, Ftp, Uri.

```csharp    
// Cách đặt tên đúng
UserGroup userGroup;
Assignment employeeAssignment;     
// Cách đặt tên cần tránh
UserGroup usrGrp;
Assignment empAssignment; 
// Các ngoại lệ
CustomerId customerId;
XmlDocument xmlDocument;
FtpHelper ftpHelper;
UriPart uriPart;
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và tránh việc viết tắt không đồng đều.***


#### 7. Sử dụng PascalCasing hoặc camelCasing (Tùy thuộc vào kiểu định danh) để viết tắt 3 ký tự hoặc hơn (2 ký đều viết hoa khi PascalCasing phù hợp hoặc có trong kiểu định danh).:

```csharp  
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer, fastFtpTransfer;
UIControl uiControl, nextUIControl;
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework. Viết hoa thu hút nhiều sự chú ý không cần thiết.***

#### 8. Không nên sử dụng dấu gạch dưới trong việc đặt tên. Ngoại lệ: Tên biến private có thể được đánh dấu với dấu gạch dưới ở đầu:

```csharp 
// Cách đặt đúng 
public DateTime clientAppointment;
public TimeSpan timeLeft;    
// Cách đặt cần tránh
public DateTime client_Appointment;
public TimeSpan time_Left; 
// Ngoại lệ (Thuộc tính private của lớp)
private DateTime _registrationDate;
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và giúp đọc code một cách tự nhiên hơn. Đồng thời tránh việc gạch chân gây chú ý không cần thiết.***

#### 9. Sử dụng các kiểu dữ liệu được định nghĩa trước (Được đặc tên bởi C#) như `int`, `float`, `string` cho việc khai báo biến cục bộ, tham số hay thuộc tính của lớp. Sử dụng kiểu dữ liệu của .NET Framework như `Int32`, `Single`, `String` khi truy cập các thành viên tĩnh của lớp như `Int32.TryParse` or `String.Join`.

```csharp
// Cách dùng đúng 
string firstName;
int lastIndex;
bool isSaved;
string commaSeparatedNames = String.Join(", ", names);
int index = Int32.Parse(input);
// Cách dùng cần tránh 
String firstName;
Int32 lastIndex;
Boolean isSaved;
string commaSeparatedNames = string.Join(", ", names);
int index = int.Parse(input);
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và khiến việc đọc code một cách dễ dàng hơn.*** 

#### 10. Sử dụng kiểu ngầm định cho các biến cục bộ. Ngoại lệ: Các biến có kiểu dữ liệu nguyên thủy (int, string, double, etc) sử dụng tên được định nghĩa trước. 

```csharp 
var stream = File.Create(path);
var customers = new Dictionary();
// Ngoại lệ
int index = 100;
string timeSheet;
bool isCompleted;
```

***Lí do: Loại bỏ lộn xộn, khó hiểu khi sử dụng kiểu dữ liệu động phức tạp. Kiểu dữ liệu có thể xem được dễ dàng khi sử dụng công cụ của Visual Studio.***

#### 11. Sử dụng danh từ hoặc cụm danh từ để đặt tên cho lớp.

```csharp 
public class Employee
{
}
public class BusinessLocation
{
}
public class DocumentCollection
{
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và dễ nhớ.***

#### 12. Sử dụng tiền tố I khi đặt tên cho Interface. Tên của Interface có thể là danh từ (cụm danh từ) hoặc tính từ.

```csharp     
public interface IShape
{
}
public interface IShapeCollection
{
}
public interface IGroupable
{
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework.***

#### 13. Đặt tên file theo tên của class chính được định nghĩa trong file. Ngoại lệ: Tên file chứa các lớp partial nên thể hiện nguồn hoặc mục đích của nó như , e.g. designer, generated, ....

```csharp 
// Located in Task.cs
public partial class Task
{
}
// Located in Task.generated.cs
public partial class Task
{
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft practices. File được sắp xếp bởi tên File theo alphabet, các lớp partial được sắp xếp liền kề.***

#### 14. Đặc tên namespace một cách có sắp xếp và có cấu trúc rõ ràng:

```csharp 
// Ví dụ
namespace Company.Technology.Feature.Subnamespace
{
}
namespace Company.Product.Module.SubModule
{
}
namespace Product.Module.Component
{
}
namespace Product.Layer.Module.Group
{
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework. Giữ cho cấu trúc code tốt.***

#### 15. Cần căn lề chính xác các dấu ngoặc nhọn theo chiều dọc: 

```csharp 
// Correct
class Program
{
  static void Main(string[] args)
  {
    //...
  }
}
```

***Lí do: Microsoft có tiêu chuẩn khác, nhưng với các nhà phát triển căn lề chính xác các dấu ngoặc nhọn theo chiều dọc được ưu tiên hơn nhiều.***

#### 16. Khai báo các thành viên của lớp ở trên đầu của định nghĩa lớp, với các biến static thì cần được đặt lên trên tất cả.

```csharp 
// Cách khai báo đúng
public class Account
{
  public static string BankName;
  public static decimal Reserves;      
  public string Number { get; set; }
  public DateTime DateOpened { get; set; }
  public DateTime DateClosed { get; set; }
  public decimal Balance { get; set; }     
  // Constructor
  public Account()
  {
    // ...
  }
}
```

***Lí do: Tìm kiếm các biến nhanh hơn, tránh việc tìm kiếm biến.***

#### 17. Sử dụng tên biến là số ít cho kiểu enums. Ngoại lệ: Enums có các trường có kiểu dữ liệu là bit.

```csharp 
// Correct
public enum Color
{
  Red,
  Green,
  Blue,
  Yellow,
  Magenta,
  Cyan
} 
// Ngoại lệ
[Flags]
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```

***Lí do: Thống nhất với cách đặt tên của  Microsoft's .NET Framework và giúp code dễ đọc hiểu code. Được đặc số nhiều vì enum có thể chứa nhiều dữ liệu (sử dụng phép toán trên bit 'OR').***

#### 18. Không nên chỉ định rõ kiểu dữ liệu của enum hay giá trị của các trường trong enum (Trừ các trường bit):

```csharp 
// Cách không nên dùng
public enum Direction : long
{
  North = 1,
  East = 2,
  South = 3,
  West = 4
} 
// Cách dùng đúng
public enum Direction
{
  North,
  East,
  South,
  West
}
```

***Lí do: Có thể tạo ra sự nhầm lẫn khi dựa và loại thực tế và các giá trị.***

#### 19. Không nên thêm hậu tố enum khi đặt tên cho enum:

```csharp     
// Cách đặt tên không nên
public enum CoinEnum
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
} 
// Cách đặt tên đúng 
public enum Coin
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và thống nhất với quy tắc không đặc mục đính sử dụng trong tên định danh.***

#### 20. Không sử dụng "Flag" hoặc "Flag" là hậu tố trong tên enum:

```csharp 
// Cách đặt tên không nên dùng 
[Flags]
public enum DockingsFlags
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
// Cách đặt tên đúng
[Flags]
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và thống nhất với quy tắc không đặc mục đính sử dụng trong tên định danh.***

#### 21. Sử dụng hậu tốt "EventArgs" khi đặt tên cho lớp chứa thông tin về sự kiện:

```csharp 
// Cách dùng đúng 
public class BarcodeReadEventArgs : System.EventArgs
{
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và dễ đọc hiểu code.***

#### 22. Đặc tên cho event handler (delegate cũng được sử dụng như là kiểu của sự kiện) phải có hậu tố "EventHandler" như ví dụ sau đây:

```csharp 
public delegate void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e);
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và dễ đọc hiểu code.***

#### 23. Không đặt tên tham số của hàm (kể cả hàm dựng) giống nhau, chỉ khác nhau ít. 

```csharp 
// Avoid
private void MyFunction(string name, string Name)
{
  //...
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework , dễ đọc hiểu code, và loại trừ các trường hợp nhầm lẫn.***

#### 24. Sử dụng 2 tham số là sender và e trong envent handlers. Tham số sender thể hiện đối tượng tạo ra event. Tham số sender thường có kiểu dữ liệu là object cho dù có thể đặc một kiểu dữ liệu cụ thể hơn:

```csharp
public void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e)
{
  //...
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và thống nhất với quy tắc không đặc mục đính sử dụng trong tên định danh.***

#### 25. Sử dụng hậu tố "Exception" cho việc đặc tên các lớp chưa thông tin về các exception:
```csharp 
// Cách đặt tên đúng 
public class BarcodeReadException : System.Exception
{
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và dễ đọc hiểu code.***

#### 26. Sử dụng các tiền tố "Any" hoặc "Is" hoặc các từ có ý nghĩa tương tự cho kiểu định danh có dữ liệu dạng boolean:

```csharp 
// Cách đặt tên đúng
public static bool IsNullOrEmpty(string value) {
    return (value == null || value.Length == 0);
}
```

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và dễ đọc hiểu code.***

#### 27. Sử dụng tên tham số của hàm khi gọi hàm:
Khi gọi một hàm, các tham số được truyền theo tên sử dụng dấu ":" và giá trị cần truyền.

```csharp
// Method
public void DoSomething(string foo, int bar) 
{
...
}

// Cách dùng cần tránh
DoSomething("someString", 1);
// Cách dùng chính xác 
DoSomething(foo: "someString", bar: 1);
```

***WLí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework và dễ đọc hiểu code. Khi sử dụng các tham số được đặt tên, chúng ta không cần đặt các tham số theo đúng thứ tự mà ta định sẵn trong hàm, vì thế chúng ta có thể đặt tham số theo bất kỳ thứ tự nào trong lời gọi hàm.

## Tài liệu tham khảo

1. [MSDN General Naming Conventions](http://msdn.microsoft.com/en-us/library/ms229045(v=vs.110).aspx)
2. [DoFactory C# Coding Standards and Naming Conventions](http://www.dofactory.com/reference/csharp-coding-standards) 
3. [MSDN Naming Guidelines](http://msdn.microsoft.com/en-us/library/xzf533w0%28v=vs.71%29.aspx)
4. [MSDN Framework Design Guidelines](http://msdn.microsoft.com/en-us/library/ms229042.aspx)
