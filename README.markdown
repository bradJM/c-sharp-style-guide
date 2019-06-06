# C# Style Guide

Adapted from [The Official raywenderlich.com C# Style Guide](https://github.com/raywenderlich/c-sharp-style-guide).

Our overarching goals are **conciseness**, **readability** and **simplicity**. Also, this guide is written to keep **Unity** in mind.

## Inspiration

This style guide is based on C# and Unity conventions.

## Table of Contents

- [Nomenclature](#nomenclature)
  + [Namespaces](#namespaces)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Parameters](#parameters--parameters)
  + [Delegates](#delegates--delegates)
  + [Events](#events--events)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Interfaces](#interfaces)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Brace Style](#brace-style)
- [Switch Statements](#switch-statements)
- [Language](#language)

## Nomenclature

On the whole, naming should follow C# standards.

### Namespaces

Namespaces are all **PascalCase**, multiple words concatenated together, without hyphens ( - ) or underscores ( \_ ). The exception to this rule are acronyms like GUI or HUD, which can be uppercase:

**AVOID:**:

```csharp
com.raywenderlich.fpsgame.hud.healthbar
```

**PREFER:**:

```csharp
RayWenderlich.FPSGame.HUD.Healthbar
```

### Classes & Interfaces

Written in **PascalCase**. For example `RadialSlider`.

### Methods

Methods are written in **PascalCase**. For example `DoSomething()`.

### Fields

All non-static fields are written **camelCase**. Per Unity convention, this includes **public fields** as well.

For example:

```csharp
public class MyClass
{
    public int publicField;
    int packagePrivate;
    private int myPrivate;
    protected int myProtected;
}
```

**AVOID:**

```csharp
private int _myPrivateVariable
```

**PREFER:**

```csharp
private int myPrivateVariable
```

Static fields are the exception and should be written in **PascalCase**:

```csharp
public static int TheAnswer = 42;
```

### Parameters

Parameters are written in **camelCase**.

**AVOID:**

```csharp
void DoSomething(Vector3 Location)
```
**PREFER:**

```csharp
void DoSomething(Vector3 location)
```

Single character values are to be avoided except for temporary looping variables.

### Delegates

Delegates are written in **PascalCase**.

When declaring delegates, DO add the suffix **EventHandler** to names of delegates that are used in events.

**AVOID:**

```csharp
public delegate void Click()
```
**PREFER:**

```csharp
public delegate void ClickEventHandler()
```

DO add the suffix **Callback** to names of delegates other than those used as event handlers.

**AVOID:**

```csharp
public delegate void Render()
```
**PREFER:**

```csharp
public delegate void RenderCallback()
```

### Events

Events should be written in **PascalCase**. Never prefix events with a prefix like **On**.

**AVOID:**

```csharp
public static event CloseCallback OnClose;
```

**PREFER:**

```csharp
public static event CloseCallback Close;
```

### Misc

In code, acronyms should be treated as words. For example:

**AVOID:**

```csharp
XMLHTTPRequest
String URL
findPostByID
```

**PREFER:**

```csharp
XmlHttpRequest
String url
findPostById
```

## Declarations

### Access Level Modifiers

Non-default access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer a single declaration per line.

**AVOID:**

```csharp
string username, twitterHandle;
```

**PREFER:**

```csharp
string username;
string twitterHandle;
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Interfaces

All interfaces should be prefaced with the letter **I**.

**AVOID:**

```csharp
RadialSlider
```

**PREFER:**

```csharp
IRadialSlider
```

## Spacing

### Indentation

Indentation should be done using **spaces** — never tabs.

#### Blocks

Indentation for blocks uses **4 spaces** for optimal readability:

**AVOID:**

```csharp
for (int i = 0; i < 10; i++)
{
  Debug.Log("index=" + i);
}
```

**PREFER:**

```csharp
for (int i = 0; i < 10; i++)
{
    Debug.Log("index=" + i);
}
```

#### Line Wraps

Indentation for line wraps should use **4 spaces** (not the default 8):

**AVOID:**

```csharp
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

**PREFER:**

```csharp
CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

### Line Length

Lines should be no longer than **100** characters long.

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity
and organization. Whitespace within methods should separate functionality, but
having too many sections in a method often means you should refactor into
several methods.

## Brace Style

All braces get their own line as it is a C# convention:

**AVOID:**

```csharp
class MyClass {
    void DoSomething() {
        if (someTest) {
          // ...
        } else {
          // ...
        }
    }
}
```

**PREFER:**

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
          // ...
        }
        else
        {
          // ...
        }
    }
}
```

Conditional statements are always required to be enclosed with braces,
irrespective of the number of lines required.

**AVOID:**

```csharp
if (someTest)
    doSomething();

if (someTest) doSomethingElse();
```

**PREFER:**

```csharp
if (someTest)
{
    DoSomething();
}

if (someTest)
{
    DoSomethingElse();
}
```
## Switch Statements

Always include a `default` case in switch statements. Cases that should "never happen" are a rich source of bugs.

**AVOID:**

```csharp
switch (variable)
{
    case 1:
        break;
    case 2:
        break;
}
```

**PREFER:**

```csharp
switch (variable)
{
    case 1:
        break;
    case 2:
        break;
    default:
        Debug.Log("This should never happen!");
        break;
}
```

## Language

Use US English spelling.

**AVOID:**

```csharp
string colour = "red";
```

**PREFER:**

```csharp
string color = "red";
```

The exception here is `MonoBehaviour` as that's what the class is actually called.
