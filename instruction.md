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

# Browser interactions
1. click
2. send keys
3. drag and drop
4. upload file
  
# Click on Element

## Find login link
![](./images/20.png)

## Clink login link
```py
from selenium import webdriver
from selenium.webdriver.common.by import By

class ClickAndSendKeys():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com"
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.get(baseUrl)
        driver.implicitly_wait(10)

        loginLink = driver.find_element(By.XPATH, "//div[@id='navbar']//a[@href='/sign_in']")
        loginLink.click()

ff = ClickAndSendKeys()
ff.test()
```

## Find email field 
![](./images/21.png)

## Find password field
![](./images/22.png)

## Send keys on email and password fields
```py
from selenium import webdriver
from selenium.webdriver.common.by import By

class ClickAndSendKeys():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com"
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.get(baseUrl)
        driver.implicitly_wait(10)

        loginLink = driver.find_element(By.XPATH, "//div[@id='navbar']//a[@href='/sign_in']")
        loginLink.click()

        emailField = driver.find_element(By.ID, "user_email")
        emailField.send_keys("test")

        passwordField = driver.find_element(By.ID, "user_password")
        passwordField.send_keys("test")


ff = ClickAndSendKeys()
ff.test()
```

## Find list of elements
![](./images/23.png)
![](./images/24.png)


## Select dropdown method if select tag exists
![](./images/25.png)

```py
from selenium import webdriver
from selenium.webdriver.support.select import Select

class DropdownSelect():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com/pages/practice"
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.get(baseUrl)
        driver.implicitly_wait(10)

        element = driver.find_element_by_id("carselect")
        sel = Select(element)

        sel.select_by_value("benz")
        print("Select Benz by value")

        sel.select_by_index("2")
        print("Select Honda by index")

        sel.select_by_visible_text("BMW")
        print("Select BMW by visible text")

        sel.select_by_index(2)
        print("Select Honda by index")


ff = DropdownSelect()
ff.test()
```

## Hidden Elements

- hidden style="display:none;"
- show style="display:blodk'"

![](./images/26.png)
![](./images/27.png)

# Useful methods and properties

## Get text inside an element
![](./images/28.png)

```py
from selenium import webdriver
from selenium.webdriver.common.by import By
import time


class GetText():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com/pages/practice"
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.implicitly_wait(10)
        driver.get(baseUrl)

        openTabElement = driver.find_element(By.ID, "opentab")
        elementText = openTabElement.text
        print("Text on element is: " + elementText)
        time.sleep(1)
        driver.quit()


ff = GetText()
ff.test()
```

## Get attributes
![](./images/29.png)

```py
from selenium import webdriver
from selenium.webdriver.common.by import By
import time


class GetAttribute():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com/pages/practice"
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.implicitly_wait(10)
        driver.get(baseUrl)

        element = driver.find_element_by_id("name")
        result = element.get_attribute("type")

        print("Value of attribute is: " + result)
        time.sleep(1)
        driver.quit()


ff = GetAttribute()
ff.test()
```

## Execute javascript
```py
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

class JavaScriptExecution():

    def test(self):
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.get("https://letskodeit.teachable.com/pages/practice")
        #driver.execute_script("window.location = 'https://letskodeit.teachable.com/pages/practice';")
        driver.execute_script("alert('hi');")

        # element = driver.find_element(By.ID, "name")
        element = driver.execute_script("return document.getElementById('name');")
        element.send_keys("Test")

ff = JavaScriptExecution()
ff.test()
```

## Take screenshot
```py
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

class Screenshots():

    def test(self):
        baseUrl = "https://letskodeit.teachable.com/"
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.get(baseUrl)
        driver.implicitly_wait(3)

        driver.save_screenshot('img.png')

ff = Screenshots()
ff.test()
```




