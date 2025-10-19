# Chain-of-Responsibility
```cs
abstract class Handler {
    protected Handler next;
    public void SetNext(Handler h)=>next=h;
    public abstract void Handle(string req);
}

class ConcreteHandler : Handler {
    public override void Handle(string req){
        if(req=="ok") Console.WriteLine("Handled");
        else next?.Handle(req);
    }
}

class Program {
    static void Main(){
        var h1=new ConcreteHandler(); var h2=new ConcreteHandler();
        h1.SetNext(h2); h1.Handle("fail"); h1.Handle("ok");
    }
}
