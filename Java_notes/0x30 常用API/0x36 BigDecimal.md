## 0x36 $BigDecimal$

- 用与解决浮点类型运算时，出现结果失真的问题

### 构造器

- `public BigDecimal(String val)` 把 $String$ 转成 $BigDecimal$


### 方法

- `public static BigDecimal valueOf(double val)` 将 $double$ 转换成 $BigDecimal$
- `public BigDecimal add(BigDecimal b)` 加法
- `public BigDecimal substract(BigDecimal b)` 减法
- `public BigDecimal multiply(BigDecimal b)` 乘法
- `public BigDecimal divide(BigDecimal b)` 除法
- `public BigDecimal divide(另一个BigDecimal对象, 精确几位, 舍入模式)` 出发，可以控制精确到小数几位
- `public double doubleValue()` 将 $BigDecimal$ 转换成 $double$

#### 用例

```java
public class Main {
    public static void main(String[] args) throws IOException {
        double a = 0.1;
        double b = 0.2;
        BigDecimal a1 = BigDecimal.valueOf(a);
        BigDecimal b1 = BigDecimal.valueOf(b);
        
        System.out.println(a1.add(b1).doubleValue());   // 0.3

        BigDecimal i = BigDecimal.valueOf(0.1);
        BigDecimal j = BigDecimal.valueOf(0.3);
        BigDecimal k = i.devide(j, 2, RoundingMode.HALF_UP);
        System.out.println(k);
    }
}
```