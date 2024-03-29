# BizCod Methods

Data model defines a data structure in terms of properties. However, the properties alone do not provide any means of processing the content of the data model. Methods are simply functions that are defined on a data model for the purpose of processing the data model content. A data model can have unlimited number of methods defined (or attached to it). Methods provide very practical and convenient ways to define functionalities proper to the data model they are defined on.

Here is a formal definition of a method.

```js

define 
    method <data-model>::<method-name>([<args>]) [ -> [variable] Type] 
        <method-body>

```

A method is defined on the data model `<data-model>`and it has to have a name `<method-name>`. It can accept the arguments `<args>` (which are optional) and might or might not return a value `[ -> variable Type]`. In addition, it has to have a body `<method-body>`. 

Let's provide a practical example of method definition. For this purpose, let's define the following data model

```js
    define
        model Part
            id Id, 
            manufacturer, 
            available Text, 
            type, 
            location, 
            condition      
```

and now, let's define a method that will identify the part condition. Specifically, we are interested whether or not the part is new or used. Let's define a method that will provide that information

```js
    define 
        method Part:isNew() -> Logical
            if (Part.condition = 'NEW') then 
                return true
            end       
            return false            
```


## Class vs Instance methods

As mentioned previously, data model (class) is an abstract definition for the purpose of providing a structure to create concrete instances of that data model (class). Therefore, there are two types of methods being `class` or `instance` method. 

A **class method** is defined on the data model itself and does not rely on any concrete instance to operate on. Conversely, an **instance** method operates on an instance and it requires a specific instance to operate on.

BizCod uses very subtle notation to differentiate between class and instance methods. A single colon `:` indicates an instance method and double colon `::` indicates a class method. 

The method `isNew` defined before is an instance method. Here is an example of a class method 

```js
    define 
        method Part::create() -> Part
            set i to instance of Part
            return i
```

This trivial class method defined on the model `Part` simply creates an instance of `Part` data model (class).

Class and instance methods serve different purposes. **Class methods** are defined on a class, and therefore, serve the purpose to provide the functionality that is in class scope. 
On the other hand, **instance methods** require a class instance and their purpose is to operate on that instance alone. 
____________________
2022 AionNEXT Corporation<br>
we build soft and you build app | <b>soft4app</b>
