---
layout: post
title: 使用Data Annotations进行手动验证
---

DataAnnotations在ASP.NET MVC中非常好用，但是其他时候，比如控制台程序，我们怎么来使用它呢，直接上代码，一个超简单的类：

```csharp
public class Customer
{
    [Required]
    public string Name { get; set; }

    [Required]
    public string Phone { get; set; }

    [Required]
    public string Email { get; set; }
}
```

下面是验证的代码：

```csharp
var cust = new Customer();
var context = new ValidationContext(cust, serviceProvider: null, items: null);
var results = new List<ValidationResult>();

var isValid = Validator.TryValidateObject(cust, context, results);

if (!isValid)
{
    foreach (var validationResult in results)
    {
        Console.WriteLine(validationResult.ErrorMessage);
    }
}
```

实现IValidatableObject，也可以：

```csharp
    public class Customer : IValidatableObject
    {
        [Required]
        public string Name { get; set; }

        [Required]
        public string Phone { get; set; }

        [Required]
        public string Email { get; set; }

        public IEnumerable<ValidationResult> Validate(ValidationContext validationContext)
        {
            ...
        }
    }
```
