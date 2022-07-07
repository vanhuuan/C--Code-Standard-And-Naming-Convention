# Tiêu chuẩn coding và cách đặt tên trong C#


| Loại dữ liệu              | Cách Viết                | Độ dài | Số nhiều | Tiền tố| Hậu tố | Viết tắt     | Kí tự hợp lệ       | Chưa dấu gạch dưới|
|:--------------------------|:-------------------------|-------:|:---------|:-------|:-------|:-------------|:-------------------|:------------------|
| Tên Namespace             | ViếtHoaCácChữCáiĐầu      |    128 | Có       | Có     | Không  | Không        | [A-z][0-9]         | Không             |
| Tên Lớp                   | ViếtHoaCácChữCáiĐầu      |    128 | Không    | Không  | Có     | Không        | [A-z][0-9]         | Không             |
| Tên Hàm dựng              | ViếtHoaCácChữCáiĐầu      |    128 | Không    | Không  | Có     | Không        | [A-z][0-9]         | Không             |
| Tên Hàm                   | ViếtHoaCácChữCáiĐầu      |    128 | Có       | Không  | Không  | Không        | [A-z][0-9]         | Không             |
| Tên Tham Số Hàm           | viếtThườngChữCáiĐầuTiên  |    128 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Không             |
| Tên Biến Cục Bộ           | viếtThườngChữCáiĐầuTiên  |     50 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Không             |
| Tên Hằng                  | ViếtHoaCácChữCáiĐầu      |     50 | Không    | Không  | Không  | Không        | [A-z][0-9]         | Không             |
| Tên Trường                | viếtThườngChữCáiĐầuTiên  |     50 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Có                |
| Tên Thuộc tính            | ViếtHoaCácChữCáiĐầu      |     50 | Có       | Không  | Không  | Có           | [A-z][0-9]         | Không             |
| Tên Delegate              | ViếtHoaCácChữCáiĐầu      |    128 | Không    | Không  | Có     | Có           | [A-z]              | Không             |
| Tên Kiểu Enum             | ViếtHoaCácChữCáiĐầu      |    128 | Có       | Không  | Không  | Không        | [A-z]              | Không             |

#### 1. Cách dùng của cách Viết Hoa Các Chữ Cái Đầu (PascalCasing) để đặt tên cho lớp và hàm:

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

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework and và dễ đọc hiểu.***

#### 2. Cách dùng của cách viết Thường Chữ Cái Đầu Tiên (camelCasing) để đặt tên cho tên thuộc tính và tên tham số hàm:

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

***Lí do: Thống nhất với cách đặt tên của Microsoft's .NET Framework and và dễ đọc hiểu.***

#### 3. Không được sư dụng cách đặt tên theo kiểu Hungarian hay bất kì các loại khác cho khai báo biến:

```csharp
// Cách đặt tên đúng
int counter;
string name;    
// Cách đặt tên cần phải tránh
int iCounter;
string strName;
```

***Lí do: Thống nhất chung với cách đặt tên của Microsoft's .NET Framework và Visual Studio IDE nhằm xác định kiểu dữ liệu dễ dàng hơn ( sử dụng công cụ của IDE).Tóm lại, bạn cần tránh đặt tên biến kèm theo kiểu dữ liệu của biến.***

#### 4. Không viết hoa tất cả các kí tự của hằng và biết readonly (chỉ đọc):

```csharp
// Cách đặt tên đúng 
public const string ShippingType = "DropShip";
// Cách đặt tên cần phải tránh
public const string SHIPPINGTYPE = "DropShip";
```

***Why: Thống nhất với cách đặt tênc của Microsoft's .NET Framework. Viết hoa thu hút quá nhiều sự chú ý.***

#### 5. Đặt tên một cách có ý nghĩa cho tên biến. Ví dụ sau đây sử dụng seattleCustomers cho customers sống ở Seattle:

```csharp
var seattleCustomers = from customer in customers
  where customer.City == "Seattle" 
  select customer.Name;
```

***Why: Thống nhất với cách đặt tên của Microsoft's .NET Framework and và dễ đọc hiểu.***

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

***Why: Thống nhất với cách đặt tên của Microsoft's .NET Framework và tránh việc viết tắt không đồng đều.***


#### 7. Sử dụng PascalCasing or camelCasing (Depending on the identifier type) for abbreviations 3 characters or more (2 chars are both uppercase when PascalCasing is appropriate or inside the identifier).:

```csharp  
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer, fastFtpTransfer;
UIControl uiControl, nextUIControl;
```

***Why: consistent with the Microsoft's .NET Framework. Caps would grab visually too much attention.***

#### 8. Do not use Underscores in identifiers. Exception: you can prefix private fields with an underscore:

```csharp 
// Correct
public DateTime clientAppointment;
public TimeSpan timeLeft;    
// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left; 
// Exception (Class field)
private DateTime _registrationDate;
```

***Why: consistent with the Microsoft's .NET Framework and makes code more natural to read (without 'slur'). Also avoids underline stress (inability to see underline).***

#### 9. Do use predefined type names (C# aliases) like `int`, `float`, `string` for local, parameter and member declarations. Do use .NET Framework names like `Int32`, `Single`, `String` when accessing the type's static members like `Int32.TryParse` or `String.Join`.

```csharp
// Correct
string firstName;
int lastIndex;
bool isSaved;
string commaSeparatedNames = String.Join(", ", names);
int index = Int32.Parse(input);
// Avoid
String firstName;
Int32 lastIndex;
Boolean isSaved;
string commaSeparatedNames = string.Join(", ", names);
int index = int.Parse(input);
```

***Why: consistent with the Microsoft's .NET Framework and makes code more natural to read.*** 

#### 10. Do use implicit type var for local variable declarations. Exception: primitive types (int, string, double, etc) use predefined names. 

```csharp 
var stream = File.Create(path);
var customers = new Dictionary();
// Exceptions
int index = 100;
string timeSheet;
bool isCompleted;
```

***Why: removes clutter, particularly with complex generic types. Type is easily detected with Visual Studio tooltips.***

#### 11. Do use noun or noun phrases to name a class. 

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

***Why: consistent with the Microsoft's .NET Framework and easy to remember.***

#### 12. Do prefix interfaces with the letter I. Interface names are noun (phrases) or adjectives.

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

***Why: consistent with the Microsoft's .NET Framework.***

#### 13. Do name source files according to their main classes. Exception: file names with partial classes reflect their source or purpose, e.g. designer, generated, etc. 

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

***Why: consistent with the Microsoft practices. Files are alphabetically sorted and partial classes remain adjacent.***

#### 14. Do organize namespaces with a clearly defined structure: 

```csharp 
// Examples
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

***Why: consistent with the Microsoft's .NET Framework. Maintains good organization of your code base.***

#### 15. Do vertically align curly brackets: 

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

***Why: Microsoft has a different standard, but developers have overwhelmingly preferred vertically aligned brackets.***

#### 16. Do declare all member variables at the top of a class, with static variables at the very top.

```csharp 
// Correct
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

***Why: generally accepted practice that prevents the need to hunt for variable declarations.***

#### 17. Do use singular names for enums. Exception: bit field enums.

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
// Exception
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

***Why: consistent with the Microsoft's .NET Framework and makes the code more natural to read. Plural flags because enum can hold multiple values (using bitwise 'OR').***

#### 18. Do not explicitly specify a type of an enum or values of enums (except bit fields):

```csharp 
// Don't
public enum Direction : long
{
  North = 1,
  East = 2,
  South = 3,
  West = 4
} 
// Correct
public enum Direction
{
  North,
  East,
  South,
  West
}
```

***Why: can create confusion when relying on actual types and values.***

#### 19. Do not use an "Enum" suffix in enum type names:

```csharp     
// Don't
public enum CoinEnum
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
} 
// Correct
public enum Coin
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
}
```

***Why: consistent with the Microsoft's .NET Framework and consistent with prior rule of no type indicators in identifiers.***

#### 20. Do not use "Flag" or "Flags" suffixes in enum type names:

```csharp 
// Don't
[Flags]
public enum DockingsFlags
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
// Correct
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

***Why: consistent with the Microsoft's .NET Framework and consistent with prior rule of no type indicators in identifiers.***

#### 21. Do use suffix EventArgs at creation of the new classes comprising the information on event:

```csharp 
// Correct
public class BarcodeReadEventArgs : System.EventArgs
{
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

#### 22. Do name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:

```csharp 
public delegate void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e);
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

#### 23. Do not create names of parameters in methods (or constructors) which differ only by the register:

```csharp 
// Avoid
private void MyFunction(string name, string Name)
{
  //...
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read, and also excludes possibility of occurrence of conflict situations.***

#### 24. DO use two parameters named sender and e in event handlers. The sender parameter represents the object that raised the event. The sender parameter is typically of type object, even if it is possible to employ a more specific type.

```csharp
public void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e)
{
  //...
}
```

***Why: consistent with the Microsoft's .NET Framework and consistent with prior rule of no type indicators in identifiers.***

#### 25. Do use suffix Exception at creation of the new classes comprising the information on exception:

```csharp 
// Correct
public class BarcodeReadException : System.Exception
{
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

#### 26. Do use prefix Any, Is, Have or similar keywords for boolean identifier:

```csharp 
// Correct
public static bool IsNullOrEmpty(string value) {
    return (value == null || value.Length == 0);
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

#### 27. Use Named Arguments in method calls:
When calling a method, arguments are passed with the parameter name followed by a colon and a value. 

```csharp
// Method
public void DoSomething(string foo, int bar) 
{
...
}

// Avoid
DoSomething("someString", 1);
// Correct
DoSomething(foo: "someString", bar: 1);
```

***Why: consistent with the Microsoft's .NET Framework and easy to read. In Named Arguments, we do not need to pass the parameters in order as defined on method definition, so we can pass the arguments in any order on method calling.***

## Offical Reference

1. [MSDN General Naming Conventions](http://msdn.microsoft.com/en-us/library/ms229045(v=vs.110).aspx)
2. [DoFactory C# Coding Standards and Naming Conventions](http://www.dofactory.com/reference/csharp-coding-standards) 
3. [MSDN Naming Guidelines](http://msdn.microsoft.com/en-us/library/xzf533w0%28v=vs.71%29.aspx)
4. [MSDN Framework Design Guidelines](http://msdn.microsoft.com/en-us/library/ms229042.aspx)
