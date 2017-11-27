---
title: "101 Csharp"
date: 2017-11-26T23:53:23+01:00
draft: true
tags: ["c#", "programming"]
title: "101 - .NET & C#"
summary: "Summary of *key* features in C#"
---

I must say that I *really* **love** C#. It wasn't my first language to learn. My first attempt was with C when I was 15 but I totally failed since I couldn't standard that thing called *pointers*. Then, I moved to VB.NET (nothing to do with just VB). That one is really easy for newbies and it's quite motivating since thanks to Visual Studio it's very easy to create UI applications. Once that more or less, I know what was to make programs, I start reading my first programming book for C++. I finished the book and I did all the exercises but I wanted to make UI apps and that's an actual pain in C++... So I found myself searching for a language with the power of C++ but with the facilities to make UI. And that was C#.

8 years later, I am now a Linux user and I don't make UI apps, only libraries and console applications. But still, C# is the most powerful language I've tried. So I want to share in this post all the **key** features of C# with respect of other languages.

But first, let's start describing what's C# and .NET.

# .NET ecosystem
.NET is a framework to create and run platform-independent and hardware-agnostic programs. It provides with a large standard library. It was developed by Microsoft withing two ISO / ECMA standards. These languages don't generate in general native code but an Intermediate bytecode that runs on runtimes virtual-machines.

The .NET languages are:

*   C#: simple and powerful object oriented language.
*   F#: functional language cross-platform.
*   VB.NET: Easy language to start learning programming.

All these languages make use of the garbage collector to manage automatically the heap memory.

## .NET implementations
The first implementation was **.NET Framework** by Microsoft. Then, as a open-source alternative **Mono** was born. Mono works almost everywhere (including the Nintendo Wii!). **Unity** took the Mono source code and they integrated it in their engine to use C# scripts. As of today, Unit stills use a quite old version of Mono, it's the equivalent for .NET Framework 3.5.

When Microsoft moved to the open-source world, they decided to create a new .NET implementation portable between platforms, so they created **.NET Core**. It works in many OS and its focus is for cloud and web.

Since there are many implementations, the .NET foundation decided to create something to unify all of them, making easier for libraries to target something and make sure it will work everywhere. This is **.NET Standard**. And it's just an *interface*. It is not an implementation. The implementations targets a version of .NET Standard depending in the API they support.

![.NET Standard](/img/posts/net_standard.jpg)

Mapping between .NET implementations and .NET Standard versions

.NET Standard  | 1.0  | 1.1  | 1.2  | 1.3  | 1.4  | 1.5   | 1.6   | 2.0
:--------------|------|------|------|------|------|-------|-------|------
.NET Core      | 1.0  | 1.0  | 1.0  | 1.0  | 1.0  | 1.0   | 1.0   | 2.0
.NET Framework | 4.5  | 4.5  |4.5.1 | 4.6  | 4.6.1| 4.6.1 | 4.6.1 | 4.6.1
Mono           | 4.6  | 4.6  | 4.6  | 4.6  | 4.6  | 4.6   | 4.6   | 5.4
Xamarin.iOS    | 10.0 | 10.0 | 10.0 | 10.0 | 10.0 | 10.0  | 10.0  | 10.14
Xamarin.Mac    | 3.0  | 3.0  | 3.0  | 3.0  | 3.0  | 3.0   | 3.0   | 3.8
Xamarin.Android| 7.0  | 7.0  | 7.0  | 7.0  | 7.0  | 7.0   | 7.0   | 8.0
UWP            | 10.0 | 10.0 | 10.0 | 10.0 | 10.0 |10.0.16|10.0.16|10.0.16
Windows        | 8.0  | 8.0  | 8.1  |      |      |       |       |
Windows Phone  | 8.1  | 8.1  | 8.1  |      |      |       |       |
Silverlight    | 8.0  |      |      |      |      |       |       |

## Terminology
Let's summarize the .NET terminology:

*   CLI: Common Language Infrastructure. The standard for IL and runtimes.
*   IL: Intermediate Language. Hardware-agnostic bytecode language. Also known as MSIL (Micrsoft IL) or CIL (Common IL).
*   BCL: Base Class Library. The System.* standard libraries in .NET.
*   CoreFx: The BCL for .NET Core.
*   CLR: Common Language Runtime. Also, the runtime for .NET Framework.
*   PCL: Portable Class Library. This was the first attempt to unify .NET platforms but only for the Microsoft implementations (.NET Framework, Xbox and Windows Phone). Deprecated by .NET Standard.
*   .NET Standard: An interface for BCL.
*   .NET Core: Another .NET implementation focus on the cloud.
*   CoreCLR: Runtime for .NET Core.
*   CoreRT: Runtime for ahead-of-time .NET compilation apps.
*   Mono: Open-source implementation for .NET Framework (including Windows UI libraries).
*   Xamarin: .NET implementation for iOS and Android.
*   C#: One of the .NET languages.
*   Assemblies: the output file with IL code. They usually have *.exe* or *.dll* extensions. Since these files are cross-platform, the extension is used also on Linux and MacOS.
*   UWP: Universal Windows Platforms. Another implementation to unify Windows platforms. The runtime is .NET Native.


## C# The Language
As said, C# is just one of the .NET languages. The compiler (*csc* on Windows and *mcs* on Linux) generates an assembly from a source file.

The extension for the sources is *.cs*. The file can contain more than one public type (more than one non-nested class, struct, enum, ...) and it doesn't have to match the file name.

# Types
Every type is either a *value type* or a *reference type*. In both case, they inherit from `System.Object` (which is a *reference type*).

![CLR Types](/img/posts/clr_types.png)

## Value Types
These types have an special behavior in the CLR. They live in the stack, there isn't any data in the heap. So the garbage collector does nothing on these types. Every time you pass a variable of these types, you are making a new copy of it. They can be: *enum* or *structs*.

### Enums
They named integer constants.
```cs
public enum FileOpenMode {
    Read,
    Write
}
```

They can be casted into integers. You can specify the integer assigned to each field. If it's not specified, then it starts from the first element (by default 0) incrementally. You can also specify which kind of integer they are:

```cs
public enum FileOpenMode : byte {
    Read = 2,
    Write = 4,
}
```

If you specify the *Flags* attribute then you can use the *enums* as *flags* and do *OR* and *AND* operations. You can use also the `HasFlag` method to check. The fields must be power of 2.
```cs
[Flags]
public enum FileOpenMode {
    Read = 1 << 0,
    Write = 1 << 1,
}

public void MyMethod()
{
    FileOpenMode mode = FileOpenMode.Read | FileOpenMode.Write;
    bool result = mode.HasFlag(FileOpenMode.Read);
}
```

Through *extension* methods you can add an actual method to the enum.
```cs
public static class FileOpenModeExtensions
{
    public static FileMode ToFileMode(this FileOpenMode openMode)
    {
        switch (openMode) {
        case FileOpenMode.Read:
            return FileMode.Open;
        case FileOpenMode.Write:
            return FileMode.Create;
        default:
            throw new ArgumentOutOfRangeException(nameof(openMode));
        }
    }
}

public void MyMethod()
{
    FileOpenMode mode = FileMode.Read;
    FileMode = mode.ToFileMode();
}
```

### Structs


#### Built-in types
The built-in types are: `bool`, `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `char`, `object` and `string`. *string* and *object* are not a *value type*.

`char` are UTF-16 codepoints, so it may not represent always a full character. `byte` are unsigned types but `sbyte` is the signed equivalent.

Note that some of these C# types are not supported in all .NET languages since they are not CLR types. This is the case for unsigned types like: `ushort`, `uint` and `ulong`. So public method and fields should not expose these types, or they should be declared with the *CLSCompliant(false)* attribute.

Struct types can be also defined by the user. They can have methods, properties and constructors and they can implement interfaces. These structures as other user-defined types, shouldn't expose public variable but use properties instead.

```cs
public struct Point
{
    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }

    public X { get; private set; }

    public Y { get; private set; }
}
```

The difference between an `struct` and a `class` is that the former goes into the stack while the latter into the heap. So struct should be small data types where it's ok to make copies of them passing to functions. Microsoft recommends to not exceed 16 bytes in structs.

#### `ref` and `out`
Since passing an *struct* to a function makes a copy, this is not always desired. There are two keywords to allow passing value types as reference, so the function can modify them in the parent scope.

*   The `ref` keyword pass any variable as reference. In the case of a *class* it will allow to give a new reference with `new`.
*   The `out` keyword is like *ref* but the method had to give any kind of value to the variable always. It's a way to enforce the initialization of a variable.

These keywords are usually used to return more than one value from a method.

#### Nullable types
As said, *struct* types cannot have the `null` value. However, we could define a *nullable* type, that is a *struct* type that also support `null`.

```cs
int i = null; // compiler error

int? i = null;  // nullable type
i = 5;  // assign values as always
bool hasValue = i.HasValue();
int j = i.Value;

int? y = null;
int w = y.GetValueOrDefault();  // returns 0
w = y ?? -1;  // assign -1 if y is null
```

#### Boxing and Unboxing
As said, *struct* inherit from `System.Object` so they can be *casted* into a *reference type*. Also, since they could implement *interfaces*, they can be also *casted* into them. Doing this kind of conversion is called *boxing* and *unboxing* and it's computational expensive since we need to create a new variable in the *heap* and copy its value there.

```cs
int i = 123;
object o = i; // boxing
int j = (int)o; // unboxing
```
![Boxing](/img/posts/boxing.png)


#### Constants
You can define as a constant any *struct* type (also *strings*). That means that the value cannot change at run-time. Refering to a constant just assign the actual value at compile-time. Therefore, if you use a constant from an external assembly like a DLL and a new version of the assembly changes the value of the constant, your program will continue to use the old value until it's recompiled again. This applies for *enums* too.


## Reference types

### Static classes

### Variable-length parameters

### Named arguments

### Generics

#### Covariance

#### Contra variance

## Type aliases
Built-in types have an alias name. Their alias name has the same functionality of the actual type (this is different to Java).
```cs
int i = 4;
System.Int32 j = 5;

int a = System.Int32.Parse("5");
int b = int.Parse("5");
```

# Anonymous methods and lambda expressions
Anonymous methods is a way to make an inline method. Similar to lambda expressions where it's like an anonymous of just one statement. Anonymous methods type can be defined from `Action<>` and `Func<>` types.

# Dynamic
Dynamic allows to use duck-typing. The type is checked at run-time. Note that a variable cannot change its type in any case.

# Var & This

# Inline conditions
Apart from the common `if` conditions there are other kind of *inline* conditionals:

## Ternary operator
As other languages, C# has the ternary operator
```cs
int a = 5;
int b = (a == 10) ? 3 : 6;
```

## Null-condition operator
If the type can be null, then we could save some code checking that condition before trying to call its methods.
```cs
Person person = null;
string first = person?.FirstName;  // this returns null
```

## Null coalesceling
Similar to the previous case, we could return different values depending if the result is null
```cs
Person person = null;
string first = person?.FirstName ?? "NoName"; // returns NoName
```

# Properties
Class fields **must** be `private`. The pattern to expose a field and be able to get or set its values is through what is called *properties*.

The only exception to this rule are *arrays*. In that case, the best-practice is to create a *getter* and/or *setter* method. The reason is that return an array to the user has the risk to have *unintended* changes in its content. This may produce unexpecting situations. So, it's safer to return a copy of the array in a *getter* method or to have a *property* returning a `ReadOnlyCollection` that doesn't allow changes.

```cs
public class File
{
    string name;  // By default, visibility is private

    public File(int id, string name)
    {
        Id = id;
        this.name = name;
        Permissions = 777;
    }

    public int Id {
        get;
        private set;  // We can change the visibility to a specific getter or setter
    }

    public string Name {
        get {
            return name;
        }
        set {
            if (!string.IsNullOrWhitespace(value))
                name = value;
        }
    }

    public int Permissions {
        get;
        set;
    }

    public int MaxNameSize { get; } = 65536;  // or from constructor

    public int MaxLength => uint.MaxValue;
}

void MyMethod()
{
    File file = new File(3, "hey");
    file.Name = "myfile";
    int id = file.Id;

    File file2 = new File(4, "other file") {
        Permissions = 644
    };
}
```

# IDisposable & Using


# IEnumerable

## Yield

# Delegates

# Events

# Asynchronous

## Old async with callbacks

## Observables

## Tasks, await

# Extension methods
An extension method is a way to add a method to a class that cannot be modified. For instance you can add methods to classes from the System namespace like *string* or *FileStream*.

# String interpolation
There are several ways to format an string:
```cs
int i = 5;
string a = "Hello " + i + " world";
a = i.ToString("X8");  // to hexadecimal padded to 8 zeros
a = string.Format("Hello {0:X} world", i);
a = $"Hello {i:X} world";
```

# StringBuilder
If you need to do several operations to make a *string*, each operation is going to create a new string in the heap memory. To save memory and time, you should use a StringBuilder.
```csharp
StringBuilder text = new StringBuilder();
text.Append("Hello");
text.AppendLine();
text.AppendFormat("{0} World!", 5);
string final = text.ToString();
```

# Exception filters
You can leverage the usage of the catch expressions by applying a condition
```cs
try {
    var responseText = await streamTask;
    return responseText;
} catch (HttpRequestException e) when (e.Message.Contains("301")) {
    return "Site Moved";
} catch (HttpRequestException e) when (e.Message.Contains("304")) {
    return "Use the Cache";
}
```

And implement loggers
```cs
public static bool LogException(this Exception e)
{
    Console.Error.WriteLine($"Exceptions happen: {e}");
    return false;
}

public void MethodThatFailsButHasRecoveryPath()
{
    try {
        PerformFailingOperation();
    } catch (Exception e) when (e.LogException()) {
        // This is never reached!
    } catch (RecoverableException ex) {
        Console.WriteLine(ex.ToString());
        // This can still catch the more specific
        // exception because the exception filter
        // above always returns false.
        // Perform recovery here
    }
}
```

# `nameof` expressions
Returns the name of the variable so you don't have to hard-code the name of the variable. Useful for exceptions:
```cs
if (string.IsNullOrWhiteSpace(lastName))
    throw new ArgumentException(message: "Cannot be blank", paramName: nameof(lastName));
```

# Usings
The common case of an `using` is to import the types from a namespace so you can reference them without their namespace.

## Static Using
The static using is a way to use fuction from static classes without referencing the class itself.

## Using alias
The using alias is a way to declare a typedef in C#. Useful when your type has many generics.

# List initializers
The list initializer allows to initialize list and dictionary easily from the constructor.

# Method overriding
There are two ways to override a method:

*   The common way is to declare any method that can be overwritten with the `virtual` keyword. Later a derived class will use the `override` keyword to make sure it's overwriting a method. The `override` keyword is optional but recommend to detect errors at compile-time.
*   The `new` keyword allows implement methods with the same signature that cannot be overwritten other way. Note that the new method will be called only if the variable has the derived type. If the same variable is casted to the base time, calling that method will call the base one.

## Operator overriding
C# allows to override operators. Usually this is done after reimplementing the `Equals` method, with the `==` and `!=` operators.

# Namespaces
A namespace is a way to classify classes in order. Usually there is a namespace per directory level in the source code.

# Abstract classes
An abstract class is a class that doesn't implement every method. These methods are marked as `abstract` and any class non-abstract derived must implement it. This is an alternative to Interfaces and it allows to implement common base functionality in derived classes.

# Indexers
Indexers are a way to implement smart arrays. It allows to any class to implement a behavior for the `[]` operator.

# Unsafe code
C# allows the use of pointers by declaring the code unsafe. Even using pointers the code is still platform agnostic. These could be use to implement critical parts of algorithm faster like in audio and image processing.

# Locks
The `lock` built-in function is a way to implement thread-safe context.

# Checked code
The `checked` built-in function provides a context where an overflow operation will produce an exception.

# IDEs
These are some free IDEs to develop C# programs:

*   Linux
    *   MonoDevelop
*   Windows
    *   Visual Studio Express / Community
    *   Xamarin Studio (MonoDevelop)
    *   SharpDevelop
*   Mac OS X
    *   Xamarin Studio (MonoDevelop)

# Debugging
IDEs is the way to debug a C# program. Debug symbols are stored in a separate file from the assembly with the *.pdb* extension. Mono was using derived format *.mdb* but now it's using *.pdb* too.

# Documentation
Although there isn't any standard, the community choose the *SandCastle* (an old Microsoft tool) style. This is the format supported by the IDE. The compiler generates a final XML file from all the documentation that later the IDE parses. Documentation comments have an XML format starting with `///`:

```cs
/// <summary>
/// Binary writer for DataStreams.
/// </summary>
public class DataWriter
```

```cs
/// <summary>
/// Initializes a new instance of the <see cref="T:Yarhl.IO.DataWriter"/> class.
/// </summary>
/// <param name="stream">Stream to write to.</param>
/// <remarks>
/// By default the endianess is LittleEndian and the encoding is UTF-8.
/// </remarks>
public DataWriter(DataStream stream)
```

# Reference
The Microsoft website provides a great documentation for .NET

*   [MSDN](https://docs.microsoft.com/en-us/dotnet/welcome)
