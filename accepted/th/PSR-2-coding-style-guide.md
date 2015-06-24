Coding Style Guide
==================

คู่มือการ Coding พื้นฐานตาม PRS- 1 สามารถเข้าดูได้ที่ [PSR-1]

เจตนาของคู่มือนี้คือ เพื่อลดความแตกต่างของการเขียน Code ที่มาจากผู้เขียนที่แตกต่างกัน
โดยเราจะแบ่งปันไฟล์ กฎ หรือ รูปแบบ ที่เราคาดหวังว่าจะให้ Code PHP ที่เราพัฒนาไปในรูปแบบเป็นแบบไหนให้กับผู้อื่น

รูปแบบและกฎที่เราได้มานั้น มาจากการตกลงร่วมกันระหว่างสมาชิกในโครงการนั้นๆ
ซึ่งเมื่อทีม มีประสบการณ์ในการทำงานร่วมกันหลายๆ โครงการมันจะทำให้เราได้ชุดรูปแบบ 1 ชุด เพื่อนำไปใช้ในโครงการที่เหลือ

ดังนั้น ประโยชน์ของคู่มือนี้ มันไม่ได้อยู่ที่ตัวกฎของตัวมันเอง แต่มันอยู่ที่การตกลงร่วมกันในการจะใช้กฎหรือรูปแบบ ร่วมกันของทีมว่าเราจะใช้แบบใหน

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119].

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md


1. Overview
-----------

- Code ต้องทำตาม คู่มือ  PSR [[PSR-1]].

- Code จะต้องใช้ 4 วรรค สำหรับย่อหน้า, ไม่ใช้ Tab

- แต่ละบรรทัด จะต้องมีตัวหนังสือไม่เกิน ค่าสูงสุดที่บังคับ และแต่ละบรรทัดไม่ควรจะมีตัวอักษรเกินค่า 120 ตัวอักษร แต่แนะนำว่าควรมีตัวหนังสือ ประมาณ 80 ตัวอักษรหรือน้อยกว่าในแต่ละบรรทัด

- จะต้องมีบรรทัดว่างหลังจากที่มีการประกาศ  namespace และจะต้องมีบรรทัดว่างหลังจากที่มีการเรียกใช้ namespace

- การเปิด ปีกกา "{" ของ class จะต้องเปิดในบรรทัดใหม่ และการ ปิดปีกกา "}" ของ class ต้องปิดในบรรทัดใหม่เช่นกัน

- การเปิด ปีกกา "{" ของ methods จะต้องเปิดในบรรทัดใหม่ และการ ปิดปีกกา "}" ของ methods ต้องปิดในบรรทัดใหม่เช่นกัน

- การใช้คำสั่ง abstract และ final จะต้องอยู่ด้านหน้า public เสมอ และถ้าจะใช้ static จะต้องไว้ด้านหลัง public เสมอ

- โครงสร้างคำสั่งสงวน จะต้องมี วรรค 1 วรรคหลังตัวมันเสมอเสมอ แต่ method และ functionที่เรียกใช้ ไม่ต้องมี

- การเปิด ปีกกา { ของโครงสร้างคำสั่ง จะต้องเปิดอยู่ในบรรทัดเดียวกับที่เริ่ม ส่วนกสนปิดปีกกา } จะต้องปิดในบรรทัดต่อไป โดยอยู่ในตำแหน่งด้านหน้า

- การเปิด วงเล็บ “(” ของ โครงสร้างคำสั่ง จะต้องไม่มี วรรค และการปิดวงเล็บ “)” ของโครงสร้างคำสั่ง จะต้องไม่มี วรรคเช่นกัน

### 1.1. Example

This example encompasses some of the rules below as a quick overview:

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

2. ข้อกำหนดทั่วไป
----------

### 2.1 หลักเกณฑ์พื้นฐานในการเขียนภาษาโปรแกรม

การเขียนภาษาโปรแกรมให้ทำตามข้อระเบียบของ [PSR-1].

### 2.2 ข้อกำหนดเกี่ยวกับไฟล์ (Files)

ทุกไฟล์ PHP ต้องใช้ UNIX LF ในการสิ้นสุดบรรทัด

ทุกไฟล์ PHP ต้องจบบรรทัดโดยการเว้นว่าง 1 บรรทัด

รูปแบบปิดเครื่องหมาย ?> ต้องตัดออกจากไฟล์ที่เป็น PHP

### 2.3. ข้อกำหนดเกี่ยวกับบรรทัด (Lines)

ความยาวของบรรทัดจะต้องไม่ยาวเกินที่กำหนดบน hard limit

ความยาวบรรทัดที่กำหนดบน soft limit ควรจะ 120 ตัวอักษร; ตัวเช็ครูปแบบจะตรวจสอบอัตโนมัติและจะต้องแจ้งเตือน แต่ไม่ควรที่จะผิดพลาด (error) ที่กำหนดบน soft limit

แต่ละบรรทัดไม่ควรยาวเกิน 80 ตัวอักษร ถ้ายาวเกินควรที่จะตัดขึ้นบรรทัดใหม่และแต่ละบรรทัดไม่เกิน 80 ตัวอักษร

ต้องไม่มีเคาะวรรคต่อท้ายของบรรทัดที่ไม่ว่าง จะต้องไม่มี

บรรทัดที่ว่างอาจจะเพิ่มเพื่อความสามารถในการอ่านและเป็นตัวบ่งบอกช่วง (บล็อก) ของชุดคำสั่ง

ต้องไม่มีชุดคำสั่งมากกว่า 1 ชุดต่อบรรทัด

### 2.4. ข้อกำหนดเกี่ยวกับย่อหน้า (Indenting)

ย่อหน้าของโปรแกรมต้องจะเคาะวรรค 4 ครั้ง และไม่ควรใช้ tab ในการย่อหน้า

> หมายเหตุ ใช้เฉพาะเคาะวรรคและไม่ควรผสมเคาะวรรคกับ tab เพื่อช่วยให้หลีกเลี่ยงปัญหาที่เกิดจาก diffs, patches, history, and annotation
> การใช้เคาะวรรคง่ายต่อการแทรกต่อการแทรก ย่อหน้ารอง (sub-indentation)
> แบบละเอียด(fine-grained) สำหรับการจัดแนวระหว่างบรรทัด (inter-line)

### 2.5. ข้อกำหนดเกี่ยวกับคำ Keyword และ True/ False / Null

คำสำคัญของ [PHP](http://php.net/manual/en/reserved.keywords.php) ควรใช้ตัวอักษรพิมพ์เล็ก

ค่าคงที่ของ PHP ได้แก่ true, false และ null ควรใช้ตัวอักษรพิมพ์เล็ก


3. Namespace และ การประกาศใช้
---------------------------------

เมื่อประกาศ `namespace` แล้วต้องเว้นว่างไว้ 1 บรรทัด

การประกาศคำสั่ง `use` ต้องอยู่หลังจากการประกาศ namespace

จากนั้นก็เว้นว่าง 1 บรรทัดแล้วบล็อกปิดคำสั่ง

ตัวอย่างเช่น

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... additional PHP code ...

```

4. Classes, Properties, and Methods
-----------------------------------
ในข้อกำหนด `คลาส` หมายรวมถึงคำสำคัญ `class`, `interface` และ `traits`

### 4.1. การสืบทอด (Extends) และการนำไปใช้ (Implements)

การประกาศใช้ `extends` และ `implements` ต้องอยู่ในบรรทัดเดียวกับชื่อคลาส

การเปิดปีกกาของคลาสต้องวางในบรรทัดต่อจากการประกาศชื่อคลาสและปิดปีกกาในบรรทัดต่อจากโค้ดภายในคลาสนั้น

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

ในการประกาศใช้ `implements` ทีละหลายรายการ สามาถแบ่งออกเป็นหลายบรรทัด
โดนในแต่ละรายการให้มีการจัดย่อหน้า `(indent)` เพียงหนึ่งครั้ง โดยให้รายการแรกอยู่ในบรรทัดถัดไป
จากการประกาศ `implements` และจะต้องมีเพียงหนึ่ง `interface` ต่อบรรทัด

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

### 4.2. ตัวแปร (Properties)

ทุกตัวแปรภายในคลาสต้องมีการประกาศค่าการมองเห็นตัวแปร `(public, protected, private)`
คำสำคัญ `var` ต้องไม่ถูกใช้ในการสร้างตัวแปร

ต้องไม่มีการประกาศตัวแปรมากกว่าหนึ่งตัวแปรในหนึ่งคำสั่ง
ชื่อตัวแปรจะต้องไม่มีคำนำหน้าตามด้วยขีดล่างเพื่อบอกค่าการมองเห็น

การประกาศตัวแปรมีลักษณะดังตัวอย่าง

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3 เมธอด

Visibility จะต้องประกาศใน เมธอดทั้งหมด

ชื่อเมธอดไม่ต้องนำหน้าด้วยขีดล่าง เพื่อใช้บอกถึงการป้องกันหรือมองเห็นเป็นส่วนตัว

ชื่อเมธอดไม่ต้องประกาศด้วยวรรคหลังชื่อเมธอด การเปิดวงเล็บปีกกาต้องอยู่บนบรรทัดของตัวเองและปีกกาปิดต้องอยู่บนบรรทัดถัดไปต่อไปนี้ตามเนื้อหา ไม่ต้องมีวรรคหลังวงเล็บเปิดและไม่ต้องมีวรรคหลังวงเล็บปิด

การประกาศเมธอดจะต้องดูสิ่งต่อไปนี้ หมายเหตุ : ตำแหน่งของวงเล็บ  คอมมา  วรรค  และวงเล็บปีกกา

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```  

### 4.4 เมธอดตัวแปรรับค่า

ในรายการอาร์กิวเมนต์ไม่ต้องมีวรรคก่อนแต่ละคอมมา และจะต้องมี 1 วรรคหลังแต่ละคอมม่า
ตัวแปรรับค่าที่มีค่าเริ่มต้นจะต้องไปที่รายกาสุดท้ายของอาร์กิวเมนต์

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

รายการอาร์กิวเมนต์อาจจะแยกออกหลายๆ บรรทัด ซึ่งแต่ละบรรทัดจะย่อหน้าเพียงครั้งเดียว  เมื่อทำเช่นนั้น ชิ้นแรกในรายการจะต้องอยู่ในบรรทัดถัดไปและจะต้องมีเพียง 1 อาร์กิวเมนต์ต่อบรรทัด

เมื่อรายการอาร์กิวเมนต์ที่ถูกแยกออกหลายๆ บรรทัด วงเล็บเปิดและวงเล็บปีกกาเปิดจะต้องอยู่รวมกันในบรรทัดของตัวเอง กับ 1 วรรคระหว่างพวกเขา

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

### 4.5 `abstract`, `final`, and `static`

เมื่อเป็นปัจจุบัน การประกาศ `abstract` และ `final` จะต้องประกาศ visibility ก่อน
เมื่อเป็นปัจจุบัน  การประกาศ `static`  จะต้องมาหลังจากการประกาศ  visibility

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```

### 4.6 เมธอดและฟังก์ชั่น Calls

เมื่อมีการทำเมธอดหรือฟังก์ชั่น Calls  ต้องไม่มีวรรคระหว่างเมธอดหรือชื่อฟังก์ชั่น และวงเล็บเปิด  ไม่ต้องมีวรรคหลังวงเล็บเปิดและต้องไม่มีวรรคก่อนวงเล็บปิด  ในรายการอาร์กิวเมนต์ไม่ต้องมีวรรคก่อนแต่ละคอมม่าและต้องมี  1  วรรค  หลังแต่ละคอมม่า

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

รายการอาร์กิวเมนต์อาจจะแยกออกหลายๆ บรรทัด ซึ่งแต่ละบรรทัดจะย่อหน้าเพียงครั้งเดียว  เมื่อทำเช่นนั้น ชิ้นแรกในรายการจะต้องอยู่ในบรรทัดถัดไปและจะต้องมีเพียง 1 อาร์กิวเมนต์ต่อบรรทัด

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5.โครงสร้างการควบคุม
---------------------

กฏของรูปแบบทั่วไปของโครงสร้างการควบคุม มีดังนี้

-	จะต้องมีช่องว่าง 1 ช่อง หลังคำสำคัญ
-	จะต้องไม่มีช่องว่างหลังเครื่องหมายวงเล็บเปิด
-	จะต้องไม่มีพื้นที่ก่อนเครื่องหมายวงเล็บปิด
-	จะต้องมีช่องว่าง 1 ช่องระหว่างเครื่องหมายวงเล็บปิด และวงเล็บเปิด
-	ส่วนของโครงสร้างจะต้องย่อหน้า 1 ย่อหน้า
-	เครื่องหมายวงเล็บปิดจะต้องมีในบรรทัดถัดไปหลังเนื้อหา

แต่ละส่วนของโครงสร้างจะต้องปิดด้วยเครื่องหมายปีกกา มาตรฐานของนี้ โครงสร้างจะมองหาและช่วยลดโอกาส ด้วยการแนะนำข้อผิดพลาดถูกเพิ่มไว้บรรทัดใหม่ของเนื้อหา

### 5.1. `if`, `elseif`, `else`

ถ้าโครงสร้างมีลักษณะดังต่อไปนี้ โปรดสังเกตุคำแหน่งของเครื่องหมายวงเล็บ วรรค และวงเล็บ

``` PHP
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```
คำสำคัญ `else if` ควรนำมาใช้แทน `else if` เพื่อให้การควบคุมคำสำคัญมีลักษณะเหมือนคำเดียว

### 5.2. `switch`, `case`

`switch` มีโครงสร้างลักษณะเหมือนต่อไปนี้ หมายเหตุ การจัดตำแหน่งของเครื่องหมายวงเล็บ, วรรค, วงเล็บ case statement จะต้องเว้นวรรค 1 วรรค ก่อน `switch` และ `break` (หรือยกเลิกคำสั่งอื่นๆ) ต้องวรรคในระดับเดียวกันของ `case` body ต้องมีความคิดเห็น เช่น // no break เมื่อเจตนาผ่าน ให้ `case` ไม่ว่างเปล่า

``` PHP
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

### 5.3. `while`, `do while`

คำสั่ง `while` มีลักษณะเหมือนต่อไปนี้ หมายเหตุ การจัดตำแหน่งของเครื่องหมายวงเล็บ, วรรค, วงเล็บ

``` PHP
<?php
while ($expr) {
    // structure body
}
```
ทำนองเดียวกัน คำสั่ง `do while` มีลักษณะเหมือนต่อไปนี้ หมายเหตุ การจัดตำแหน่งของเครื่องหมายวงเล็บ, วรรค, วงเล็บ
``` PHP
<?php
do {
    // structure body;
} while ($expr);
```

### 5.4. `for`

คำสั่ง `for` มีลักษณะเหมือนต่อไปนี้ หมายเหตุ การจัดตำแหน่งของเครื่องหมายวงเล็บ, วรรค, วงเล็บ

``` PHP
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 5.5. `foreach`

คำสั่ง `foreach` มีลักษณะเหมือนต่อไปนี้ หมายเหตุ การจัดตำแหน่งของเครื่องหมายวงเล็บ, วรรค, วงเล็บ

``` PHP
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 5.6. `try`, `catch`

กลุ่ม `try` และ `catch` มีลักษณะเหมือนต่อไปนี้ หมายเหตุ การจัดตำแหน่งของเครื่องหมายวงเล็บ, วรรค, วงเล็บ

``` PHP
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

6. Closures
-----------

หลังจากประกาศ `Function` จะต้องตามด้วย `Space` และใช้ Space ก่อนและหลังการใช้ Use

การเปิด `ปีกกา` จะต้องอยู่บรรทัดเดียวกับ Function และการปิด `ปีกกา` จะต้องอยู่บรรทัดถัดมาจาก Body

เมื่อทำการเปิด `วงเล็บ` ให้ใส่ Argument List หรือ Variable List ต่อจาก วงเล็บ ได้เลยโดยไม่ต้องมี Space และเมื่อทำการประกาศ Argument List หรือ Variable List เสร็จเรียบร้อยแล้วให้ทำการปิดวงเล็บได้เลย โดยไม่ต้องมี `Space` เช่นกัน

ภายใน `Argument List` และ `Variable List` จะไม่ใช้ Space ก่อนเครื่องหมาย Comma(,) แต่จะเคาะ 1 Space หลัง Comma(,) แทน

เมื่อต้องการประกาศค่าเริ่มต้นต้องนำไปไว้ที่ท้ายของ Argument List

ตัวอย่างการวางตำแหน่ง `วงเล็บ, Commas, เว้นวรรค และ ปีกกา`

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```

เมื่อต้องการแยกบรรทัดของ `Argument List` หรือ `Variable List` ให้ประกาศใช้บรรทัดหลังต่อจากชื่อ Function และต้องมี Argument หรือ Variable บรรทัดละตัวเท่านั้น และเรียงความยาวของ Argument หรือ Variable จากน้อยไปมาก

เมื่อสิ้นสุดการประกาศ `Argument List` หรือ `Variable List` ที่มีลักษณะแยกบรรทัด จะทำการปิด วงเล็บ และเปิด ปีกกา ในบรรทัดถัดมา และจะเคาะ 1 Space ระหว่าง วงเล็บ และ ปีกกา

ตัวอย่างการปิด Argument List และ Variable List ทั้งแบบแยกบรรทัด และไม่แบ่งบรรทัด

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

โปรดทราบว่ากฎการจัดรูปแบบนอกจากนี้ยังนำไปใช้สำหรับการเรียกใช้ Function หรือ Method โดยตรงด้วย

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```


7. ข้อสรุป
--------------

มีหลายองค์ประกอบของรูปแบบ และละเว้นการปฏิบัติจากคู่มือนี้ แต่ไม่จำกัดเฉพาะ

- การประกาศของ global variables และ global constants

- การประกาศของ Functions

- Operators และ assignment

- การจัดตำแหน่งระหว่างบรรทัด (Inter-line alignment)

- การเขียนอธิบาย และเอกสาร

- คำนำหน้าและ คำต่อท้ายของชื่อ Class

- แนวทางการปฏิบัติที่ดี

ในอนาคตอาจมีการปรับแก้คู่มือเพื่อที่อยู่เหล่านั้น หรือองค์ประกอบอื่น ๆ ของรูปแบบ และแนวทางการปฏิบัติ


Appendix A. Survey
------------------

In writing this style guide, the group took a survey of member projects to
determine common practices.  The survey is retained herein for posterity.

### A.1. ข้อมูลการสำรวจ (Survey Data)

    url,http://www.horde.org/apps/horde/docs/CODING_STANDARDS,http://pear.php.net/manual/en/standards.php,http://solarphp.com/manual/appendix-standards.style,http://framework.zend.com/manual/en/coding-standard.html,http://symfony.com/doc/2.0/contributing/code/standards.html,http://www.ppi.io/docs/coding-standards.html,https://github.com/ezsystems/ezp-next/wiki/codingstandards,http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html,https://github.com/UnionOfRAD/lithium/wiki/Spec%3A-Coding,http://drupal.org/coding-standards,http://code.google.com/p/sabredav/,http://area51.phpbb.com/docs/31x/coding-guidelines.html,https://docs.google.com/a/zikula.org/document/edit?authkey=CPCU0Us&hgd=1&id=1fcqb93Sn-hR9c0mkN6m_tyWnmEvoswKBtSc0tKkZmJA,http://www.chisimba.com,n/a,https://github.com/Respect/project-info/blob/master/coding-standards-sample.php,n/a,Object Calisthenics for PHP,http://doc.nette.org/en/coding-standard,http://flow3.typo3.org,https://github.com/propelorm/Propel2/wiki/Coding-Standards,http://developer.joomla.org/coding-standards.html
    voting,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,no,no,no,?,yes,no,yes
    indent_type,4,4,4,4,4,tab,4,tab,tab,2,4,tab,4,4,4,4,4,4,tab,tab,4,tab
    line_length_limit_soft,75,75,75,75,no,85,120,120,80,80,80,no,100,80,80,?,?,120,80,120,no,150
    line_length_limit_hard,85,85,85,85,no,no,no,no,100,?,no,no,no,100,100,?,120,120,no,no,no,no
    class_names,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,lower_under,studly,lower,studly,studly,studly,studly,?,studly,studly,studly
    class_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,next,next,next,next,next,next,same,next,next
    constant_names,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper
    true_false_null,lower,lower,lower,lower,lower,lower,lower,lower,lower,upper,lower,lower,lower,upper,lower,lower,lower,lower,lower,upper,lower,lower
    method_names,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,lower_under,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel
    method_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,same,next,next,next,next,next,same,next,next
    control_brace_line,same,same,same,same,same,same,next,same,same,same,same,next,same,same,next,same,same,same,same,same,same,next
    control_space_after,yes,yes,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes
    always_use_control_braces,yes,yes,yes,yes,yes,yes,no,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes
    else_elseif_line,same,same,same,same,same,same,next,same,same,next,same,next,same,next,next,same,same,same,same,same,same,next
    case_break_indent_from_switch,0/1,0/1,0/1,1/2,1/2,1/2,1/2,1/1,1/1,1/2,1/2,1/1,1/2,1/2,1/2,1/2,1/2,1/2,0/1,1/1,1/2,1/2
    function_space_after,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no
    closing_php_tag_required,no,no,no,no,no,no,no,no,yes,no,no,no,no,yes,no,no,no,no,no,yes,no,no
    line_endings,LF,LF,LF,LF,LF,LF,LF,LF,?,LF,?,LF,LF,LF,LF,?,,LF,?,LF,LF,LF
    static_or_visibility_first,static,?,static,either,either,either,visibility,visibility,visibility,either,static,either,?,visibility,?,?,either,either,visibility,visibility,static,?
    control_space_parens,no,no,no,no,no,no,yes,no,no,no,no,no,no,yes,?,no,no,no,no,no,no,no
    blank_line_after_php,no,no,no,no,yes,no,no,no,no,yes,yes,no,no,yes,?,yes,yes,no,yes,no,yes,no
    class_method_control_brace,next/next/same,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/next,same/same/same,same/same/same,same/same/same,same/same/same,next/next/next,next/next/same,next/same/same,next/next/next,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/same,next/next/next

### A.2. หัวข้อการสำรวจ (Survey Legend)

`indent_type`:
ย่อหน้า tab =  2 หรือ 4 วรรค

`line_length_limit_soft`:
ความยาวของตัวอักษรไม่ควรเกินกี่ตัวอักษร `?` = ไม่แสดงความคิดเห็น `no` = ไม่จำกัด

`line_length_limit_hard`:
ความยาวของตัวอักษรจะต้องไม่เกินกี่ตัวอักษร `?` = ไม่แสดงความคิดเห็น `no` = ไม่จำกัด

`class_names`:
การตั้งชื่อ class `lower` = ใช้ตัวอักษรเล็กทั้งหมด `lower_under` = ตัวอักษรเล็กทั้งหมดมีขีดล่างคั่น `studly` = StudlyCase

`class_brace_line`:
การเปิดวงเล็บปีกกาของ class `same` = บรรทัดเดี๋ยวกับชื่อ class `next` = บรรทัดถัดไปจากชื่อ class

`constant_names`:
การตั้งชื่อ class constants `upper` = ตัวอักษรใหญ่ทั้งหมดมีขีดล่างคั่น

`true_false_null`:
`true`, `false` และ `null` ให้คำสำคัญนี้เป็น `lower` = ตัวเล็กทั้งหมด หรือ `upper` = ตัวใหญ่ทั้งหมด

`method_names`:
การตั้งชื่อ methods `camel` = camelCase, `lower_under` = ตัวอักษรเล็กทั้งหมดมีขีดล่างคั่น

`method_brace_line`:
การเปิดวงเล็บปีกกาของ method `same` = บรรทัดเดี๋ยวกับชื่อ method `next` = บรรทัดถัดไป

`control_brace_line`:
การเปิดวงเล็บปีกกาของ control structure `same` = บรรทัดเดี๋ยวกับชื่อ control structure `next` = บรรทัดถัดไป

`control_space_after`:
มีช่องว่างหลังคำสำคัญของ control structure

`always_use_control_braces`:
control structures จะไม่ใช้วงเล็บ

`else_elseif_line`:
เมื่อมีการใช้ `else` หรือ `elseif` `same ` = วงเล็บปีกกาไม่อยู่บรรทัดเดียวกัน หรือ `next` = ไม่อยู่ในบรรทัดถัดไป

`case_break_indent_from_switch`:
`case` และ `break` อยู่เยื้องจากคำสั่ง `switch` เท่าไร

`function_space_after`:
`function calls` จะมีช่องว่างหลังชื่อฟังก์ชั่น และก่อนวงเล็บเปิด

`closing_php_tag_required`:
ในไฟล์ที่มีเพียง PHP จะปิด `?>` หรือไม่

`line_endings`:
ประเภทของการสิ้นสุดบรรทัดใช้อย่างไร

`static_or_visibility_first`:
เมื่อประกาศ method `static` จะมาก่อน หรือ `visibility`

`control_space_parens`:
ในการแสดง control structure จะมีช่องว่างหลังวงเล็บเปิดและช่องว่างก่อนที่จะวงเล็บปิด `yes` = if ( $expr ), `no` = if ($expr)

`blank_line_after_php`:
มีบรรทัดว่างหลังจากแท็กเปิด PHP แท็ก

`class_method_control_brace`:
บทสรุปการเปิดวงเล็บปีกกาของ classes, methods, and control structures.


### A.3. ผลลัพธ์การสำรวจ (Survey Results)

    indent_type:
        tab: 7
        2: 1
        4: 14
    line_length_limit_soft:
        ?: 2
        no: 3
        75: 4
        80: 6
        85: 1
        100: 1
        120: 4
        150: 1
    line_length_limit_hard:
        ?: 2
        no: 11
        85: 4
        100: 3
        120: 2
    class_names:
        ?: 1
        lower: 1
        lower_under: 1
        studly: 19
    class_brace_line:
        next: 16
        same: 6
    constant_names:
        upper: 22
    true_false_null:
        lower: 19
        upper: 3
    method_names:
        camel: 21
        lower_under: 1
    method_brace_line:
        next: 15
        same: 7
    control_brace_line:
        next: 4
        same: 18
    control_space_after:
        no: 2
        yes: 20
    always_use_control_braces:
        no: 3
        yes: 19
    else_elseif_line:
        next: 6
        same: 16
    case_break_indent_from_switch:
        0/1: 4
        1/1: 4
        1/2: 14
    function_space_after:
        no: 22
    closing_php_tag_required:
        no: 19
        yes: 3
    line_endings:
        ?: 5
        LF: 17
    static_or_visibility_first:
        ?: 5
        either: 7
        static: 4
        visibility: 6
    control_space_parens:
        ?: 1
        no: 19
        yes: 2
    blank_line_after_php:
        ?: 1
        no: 13
        yes: 8
    class_method_control_brace:
        next/next/next: 4
        next/next/same: 11
        next/same/same: 1
        same/same/same: 6
