# Adapter - Патерн Проєктування

Патерн **Adapter** дозволяє одному об’єкту працювати з іншим, **інтерфейси яких не сумісні**, шляхом «обгортання» одного об’єкта іншим.

Це подібно до перехідника між розетками різних стандартів:  
✅ новий інтерфейс → працює з існуючим класом без змін його коду.

---

## Ідея патерна

> Забезпечити взаємодію об’єктів із **несумісними інтерфейсами**, шляхом створення адаптера, який «перекладає» виклики.

---

## Структура

| Роль       | Опис |
|------------|------|
| `ITarget`  | Цільовий інтерфейс, який очікує клієнт |
| `Adaptee`  | Клас з «несумісним» інтерфейсом |
| `Adapter`  | Адаптер, що перетворює інтерфейс `Adaptee` у `ITarget` |

---

## Код

```csharp
interface ITarget { 
    void Request(); 
}

class Adaptee { 
    public void SpecificRequest() => Console.WriteLine("Specific request"); 
}

class Adapter : ITarget {
    private Adaptee _adaptee = new();
    public void Request() => _adaptee.SpecificRequest();
}

class Program { 
    static void Main() => new Adapter().Request(); 
}
## Клієнт очікує метод Request(), але в Adaptee є SpecificRequest().
