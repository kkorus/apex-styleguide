# Apex Styleguide #


This document contains apex styleguide.

1. Apex Basics
1.1. Naming
1.2. Code structure
2. Unit Testing
3. Triggers
4. Visualforce
5. Object Names and custom Fields

----------

## Apex Basics ##

###  Naming ###

Identifier 	  | Case
------------- | -------------
Class | Pascal
Enum type  | Pascal
Enum value| Pascal
Exception class | Pascal
Interface  | Pascal
Methods | Camel


- Use PascalCase naming convetions for naming Classes.

> **Note:**  
> - Use a noun or noun phrase to name a class.
> - Use abbreviations sparingly.
> - Do not use the underscore character (_).
```
public class AccountPlanService {
  // ...
}
```

- Use camelCase naming convetions for methods, variables and properties in Apex.

> **Note:**  - Built-in types start with capital letter, eg ID, Integer, String. Methods verbs.

```
private String myPrivateField;

public Integer myPublicProperty {
	get { return prop; }
	set { prop = value;
}

public static void calculateRisks() {
  Integer localVariable = 0;
}
```

- Don't use set, list, .etc while naming variable storing collections.
```
// avoid
List<Account> accountsList = new List<Account>();
Set<String> namesSet = new Set<String>();
Map<ID, Opporunity> opportunitiesMap = new Map<ID, Opportunity>();

// recommended 
List<Account> accounts = new List<Account>();
Set<String> names = new Set<String>();
Map<ID, Opporunity> opportunities= new Map<ID, Opportunity>();
```

- Use meaningful names for yours variables.
```
Boolean isWinner = true;
```

### Code structure ###

- Put accessible members Up Top. It will make code easier to read and helps identify which members of a class can be called and unit tested.

```
public class AccountPlanService {
  public Integer calculateRisks() {
    return innerPrivateMethod();
  }
  
  private Integer innerPrivateMethod() {
    // ...
  }
}
```

- For complex if statements assign 

```
Boolean isValid = 
```
----------

Unit Testing
--------

----------

Triggers
--------

----------

Visualforce
--------

----------
