# Understanding Elements and DOM
- use chrometools and use inspect

# Find Element By Id

![](./images/1.png)
```py
from selenium import webdriver

class FindByIdName():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com/pages/practice"
        driver = webdriver.Chrome()
        driver.get(baseUrl)
        elementById = driver.find_element_by_xpath("//*[@id='name']")

        if elementById:
            print('Found ID')

ff = FindByIdName()
ff.test()
```

# Find List of Elements
![](./images/2.png)
```py
from selenium import webdriver
from selenium.webdriver.common.by import By

class ListOfElements():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com/pages/practice"
        driver = webdriver.Chrome()
        driver.get(baseUrl)

        text_type = driver.find_elements_by_xpath("//*[@type='text']")
        
        print(len(text_type))


ff = ListOfElements()
ff.test()
```

# XPath

> Syntax

> //tag[@attribute='value']

## // and /
![](./images/3.png)
### / immediate child
![](./images/4.png)

### // nested child
![](./images/5.png)

## Using Text
> Syntax

> //tag[@attribute='value']//tag[text()='Required Text']

> //tag[text()='Required Text']

![](./images/6.png)

## Using Contains
> Syntax

> //tag[@attribute='value']//tag[contains(attribute, 'value')]

> //tag[contains(attribute, 'Partial Text')]

![](./images/8.png)
![](./images/9.png)
![](./images/10.png)

## Using Starts-with
> Syntax

> //tag[starts-with(attribute, 'value')]

![](./images/11.png)
![](./images/12.png)

## Simplify xpath
![](./images/13.png)
![](./images/14.png)


## Parent and sibling

> Syntax

> xpath-to-some-element//parent::<tag>

> xpath-to-some-element//preceding-sibling::<tag>

> xpath-to-some-element//following-sibling::<tag>

![](./images/14.png)
### Parent
![](./images/15.png)

### Preceding sibling
![](./images/16.png)

### Following-sibling
![](./images/17.png)


## Exercise
1. Find the price of the course "Python Programming Language" in http://letskodeit.teachable.com/pages/practice
![](./images/18.png)

2. Find atuhor of the book "The Green Mile" in http://dhtmlx.com/docs/products/dhtmlxGrid/	
![](./images/19.png)
  



