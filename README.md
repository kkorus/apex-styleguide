# Apex Style Guide #

This document contains apex style guide. Begining from naming convetions, code structure to best practices. You don't have to stick rigidly to this rules. Make any modifications that fits you better, only be consistent.

## Table of Contents ##

1. Apex Basics
2. Unit Testing
3. Triggers
4. Visualforce
5. Object Names and custom Fields

----------

## Apex Basics ##

###  Prefixes ###




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

```java
public class AccountPlanService {
  // ...
}
```

- Interface name should start with capital  `I` letter and follow the same rules as Classes. 
```java
public interface IPurchaseOrder {
    Double discount();
}
```

- Use camelCase naming convetions for methods, variables and properties in Apex.

> **Note:**  
> - Built-in types should start with capital letter like ID, Integer, String. 
> - Use verbs or verb phrases to name methods.

```java
private String myPrivateField;

public Integer myPublicProperty {
	get { return prop; }
	set { prop = value;
}

public static void myPublicMethod() {
  Integer localVariable = 0;
}
```

- Don't use `set`, `list`, `map` keywords for naming variable storing collections.
```java
// avoid
List<Account> accountsList = new List<Account>();
Set<String> namesSet = new Set<String>();
Map<ID, Opporunity> opportunitiesMap = new Map<ID, Opportunity>();

// recommended 
List<Account> accounts = new List<Account>();
Set<String> names = new Set<String>();
Map<ID, Opporunity> opportunities= new Map<ID, Opportunity>();
```

- Constant variables should be all uppercase with words seperated by underscore (_).
```java
private static final Integer MONTHS_COUNT = 12;
```

- Use meaningful names for yours variables.
```java
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
    return 1;
  }
}
```

- For complex if statements assign todo..

```
Boolean isValid = 
```
----------

## Unit Testing ##

### Naming ###

- Add `Test` suffix to test class name.

```java
@isTest
public class MyServiceTest {
 // ...
}
```

- Name test methods with `test<methodOrFunctionalityUnderTest><ShortTestCaseDesc>` pattern. For example: 

> **Note:**  Use `@isTest` attribute rather than `testMethod` keyword.
```java
@isTest
public static void testSavingOpportunityWithoutTechonlogiesFieldRaiseError() {}
```

### Code structure ###

- Use `Arrange`, `Act`, `Assert` pattern for unit test methods.

> **Note:**  
- Code that would be tested is placed between `Test.startTest()` and `Test.stopTest()`.

```java
@isTest
public static void testAddingMoreThenOneAccountPlanForAccountRaiseError() {
    // Arrange
    List<Account> accounts = new List<Account>();
    for(Integer i = 0; i < 20; i++) {
        accounts.add(new Account(Name = 'Account' + i));
    }
    insert accounts;
    
    // Act
    Test.startTest();
    Database.SaveResult[] result = Database.insert(accounts , false);
    Test.stopTest();
    
    // Assert                
    for(Integer i = 0; i < result .size(); i++) {         
        System.assert(result[i].isSuccess());
    }
}  
```

----------

Triggers
--------

----------

Visualforce
--------

----------
