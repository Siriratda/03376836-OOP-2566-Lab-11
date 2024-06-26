# Lab 11 Exercise 7

## Prevent inheritance by keyword `sealed`

1.สร้าง console application project

```cmd
dotnet new console --name Lab11_Ex07
```

2.เปลี่ยน code ให้เป็นดังต่อไปนี้

```cs
Derived_2 d2 = new Derived_2();
Base b = (Base) d2;
Derived_1 d1 = (Derived_1) d2;

b.A();
d1.A();
d2.A();

class Base
{
    public virtual void A()
    {
        System.Console.WriteLine("Base.A()");
    }
}
class Derived_1 : Base
{
    public sealed override void A()
    {
        System.Console.WriteLine("Derived_1.A()");
    }
}
class Derived_2 : Derived_1
{
    public override void A()
    {
        System.Console.WriteLine("Derived_2.A()");
    }
}
```

3.Build project โดยการใช้คำสั่ง

```cmd
dotnet build  Lab11_Ex07
```

ถ้ามีที่ผิดพลาดในโปรแกรม ให้แก้ไขให้ถูกต้อง

4.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 3

![7](https://github.com/Siriratda/03376836-OOP-2566-Lab-11/assets/144195995/99b7d542-0ff7-4e8b-be71-9c0057eb6db9)

ไม่สามารถ Build ได้ เพราะ Derived_2.A พยายามจะสืบทอดจาก Derived_1 แต่ถูกปิดกั้นด้วยคำสั่ง sealed แก้โดยลบส่วนการทำงานของclass Derived_2 : Derived_1 ออก

5.Run project โดยการใช้คำสั่ง

```cmd
dotnet run --project Lab11_Ex07
```

6.บันทึกผลที่ได้จากการรันคำสั่งในข้อ 5

![7 1](https://github.com/Siriratda/03376836-OOP-2566-Lab-11/assets/144195995/0337d6c5-4e46-4470-a5df-dda52be8cd72)

7.อธิบายสิ่งที่พบในการทดลอง

ไม่สามารถ Run ได้ เพราะ Derived_2.A พยายามจะสืบทอดจาก Derived_1 แต่ถูกปิดกั้นด้วยคำสั่ง sealed แก้โดยลบส่วนการทำงานของclass Derived_2 : Derived_1 ออก

โปรแกรมจะแสดงผล

Derived_1.A()

Derived_1.A()

Derived_1.A()
