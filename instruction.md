# Understanding Elements and DOM
- use chrometools and use inspect

# Find Element By Id

## By Id
```html
<input id="name" name="enter-name" class="inputs" placeholder="Enter Your Name" type="text">
```
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



