This code shows an interresting example where I was able to control a
variable used inside a private member using an overrided virtual method
which I controled

The virtual method

`       System.Collections.ArrayList.set_Capacity`

is used in

`       private System.Void System.Collections.ArrayList::EnsureCapacity(System.Int32)`

and can be invoked from (i.e. it isused by)

`       System.Collections.ArrayList.Add(Object) : Int32`
`       System.Collections.ArrayList.Insert(Int32, Object) : Void`
`       System.Collections.ArrayList.InsertRange(Int32, ICollection) : Void`

so by overriding the public method I am able to afect the behaviour of a
private method (which I don't have access to)

In this example bellow I override the ArrayList's Capacity method which
is then invoked by the private method private ArrayList.EnsureCapacity
(which was invoked by the public method ArrayList.Add)

`using System;`
`using System.IO;`
`using System.Reflection;`

`namespace Owasp`
`{`

`   class myOverride : System.Collections.ArrayList`
`   {`
`       public override int Capacity`
`       {`
`           set`
`           {`
`               Console.WriteLine("Inside  myOverride.set_Capacity (the method under our control)");`
`               base.Capacity = base.Capacity+1;`
`               Console.WriteLine("\n Current Stack trace (note that  System.Collections.ArrayList.EnsureCapacity(Int32 min) is a private method)\n");                `
`               Console.WriteLine(new System.Diagnostics.StackTrace().ToString());`
`           }`
`           get`
`           {`
`               Console.WriteLine("Inside  myOverride.get_Capacity");`
`               return base.Capacity;`
`           }`
`       }`
`       public override string ToString()`
`       {`
`           Console.WriteLine("ToString() invoked");`
`           return base.ToString();`
`       }`
`   }`
`   class ArrayCapacity_Test`
`   {`
`       public static void Main()`
`       {`
`   `
`           System.Collections.ArrayList myOver = new myOverride();            `
`           try`
`           {`
`               myOver.Add("test");`
`           //    Console.WriteLine(myOver.Capacity);`
`           }`
`           catch (Exception Ex)`
`           {`
`               Console.WriteLine(Ex.Message);`
`               Console.WriteLine(Ex.StackTrace);`
`           }`
`       }`
`   }`
`}`

(from Reflector) sourcecode of private System.Void
System.Collections.ArrayList::EnsureCapacity(System.Int32)

`private void EnsureCapacity(int min)`
`{`
`     if (this._items.Length < min)`
`     {`
`           int num1 = (this._items.Length == 0) ? 0x10 : (this._items.Length * 2);`
`           if (num1 < min)`
`           {`
`                 num1 = min;`
`           }`
`           this.Capacity = num1;`
`     }`
`}`

(from Reflector) sourcecode of private System.Void
System.Collections.ArrayList::Add(System.object)

`public virtual int Add(object value)`
`{`
`     if (this._size == this._items.Length)`
`     {`
`           this.EnsureCapacity(this._size + 1);`
`     }`
`     this._items[this._size] = value;`
`     this._version++;`
`     return this._size++;`
`}`

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")