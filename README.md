# Adapter
```cs
interface ITarget { void Request(); }
class Adaptee { public void SpecificRequest()=>Console.WriteLine("Specific request"); }

class Adapter : ITarget {
    private Adaptee _adaptee = new();
    public void Request()=>_adaptee.SpecificRequest();
}

class Program { static void Main()=>new Adapter().Request(); }
