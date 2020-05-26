![icon](icon.png)

# ComponentSchema
This command line tool uses reflection to generate .schema files for your custom actions.

## Installation
To install:

```dotnet tool install componentschema```

In your project add System.Data.Annotations package

```dotnet add package System.Data.Annotations```

This tool will generate .schema files for all public dialogs with a public const Kind.

```csharp
    [Description("Create a container")]
    public class MyAction : Dialog
    {
        [JsonProperty("$kind")]
        public const string Kind = "Iciclecreek.MyAction";

        [JsonProperty("disabled")]
        [Description("Disable this action")]
        public BoolExpression Disabled { get; set; }
    }
```

Supported attributes

| Attribute                        | Purpose                                                 |
|----------------------------------|---------------------------------------------------------|
| **[DisplayName("title")]**       | set alternate title (Default is name of class/property) |
| **[Description("description")]** | set the description                                     |
| **[Required]**                   | mark that a property is required                        |
| **[DefaultValue(defaultValue)]** | set the default value for a property                    |
| **[Range(minValue,maxValue)]**   | put a constraint on the min/max value for a number      |
| **[StringLength(min,max)]**      | put a constraint on length string for a property        |
| **[MinLength(minLength)]**       | put a constraint on the length of a property            |
| **[MaxLength(maxLength)]**       | put a constriant on the lenght of a property            |

## output
Each class will have a .schema file generated with name of the == value of $kind.
It will also generate a ComponentRegistration class.
 