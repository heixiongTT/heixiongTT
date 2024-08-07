## java.utils.Date和java.time.LocalDate互相转换

将 `Date` 转换为 `LocalDate` 在 Java 中是常见的任务。`Date` 类是旧版的日期类，而 `LocalDate` 类是 Java 8 引入的新日期和时间 API 中的一部分，它们提供了更好的日期和时间处理方法。以下是将 `Date` 转换为 `LocalDate` 的方法：

### 使用 `Instant` 和 `ZoneId`

1. **通过 `Date` 获取 `Instant`**：
   
   - `Date` 对象可以转换为 `Instant` 对象，`Instant` 表示一个时间点（精确到纳秒）。

2. **通过 `Instant` 获取 `LocalDate`**：
   
   - 使用系统默认的时区（`ZoneId.systemDefault()`）将 `Instant` 转换为 `LocalDate`。

以下是示例代码:

```
import java.time.Instant;
import java.time.LocalDate;
import java.time.ZoneId;
import java.util.Date;

public class DateToLocalDateExample {
    public static void main(String[] args) {
        // 示例日期
        Date date = new Date();

        // 将 Date 转换为 Instant
        Instant instant = date.toInstant();

        // 获取系统默认时区的 ZoneId
        ZoneId zoneId = ZoneId.systemDefault();

        // 将 Instant 转换为 LocalDate
        LocalDate localDate = instant.atZone(zoneId).toLocalDate();

        // 合并成一行
        date.toInstant().atZone(zoneId).toLocalDate();

        // 输出结果
        System.out.println("Date: " + date);
        System.out.println("LocalDate: " + localDate);
    }
}
```


