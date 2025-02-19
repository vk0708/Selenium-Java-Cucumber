# Automation with Selenium Java with Cucumber and Frameworks

## Index  
1. [Selenium](#what-is-selenium)  
2. [Web Driver and Maven Project](#webdriver)  
3. [Web Elements and Locators](#web-elements--locators-in-selenium)
4. [Test Cases for Amazon Product Search](#amazon-product-search-automation) 

## What is Software Testing?
• Software testing is an activity to check whether the actual results match the 
expected results and to ensure that the software system is Defect free. 
• Software testing also helps to identify errors, gaps or missing requirements in 
contrary to the actual requirements. 
• It can be either done manually or using automated tools.

![image](https://github.com/user-attachments/assets/f36e9868-66ed-453c-a00a-6a435f0fd891)

## What is selenium?
• Selenium is a free (open source) automated testing suite for web applications across different browsers and platforms.
• Testing done using Selenium tool is usually referred as Selenium Testing.
• Selenium is not just a single tool but a suite of software's.
• It has four components:
   Selenium Integrated Development Environment (IDE)
   Selenium Remote Control (RC)
   WebDriver
   Selenium Grid

 ## Advantages of Selenium
• Selenium is pure open source tool.
• Selenium supports variety of languages that include Java, Perl, Python, C#, Ruby, Groovy, Java Script, and VB Script. etc.
• Selenium supports many operating systems like Windows, Macintosh, Linux, Unix etc.
• Selenium supports many browsers like Internet explorer, Chrome, Firefox, Opera, Safari etc.
• Selenium can be integrated with Jenkins or Hudson for continuous integration.
• Selenium can be integrated with other open source tools for supporting other features.
• Selenium can be used for Android, IPhone, Blackberry etc. based application testing.

## Disadvantages of Selenium
• We can use Selenium only to test web applications. We cannot test desktop applications.

![image](https://github.com/user-attachments/assets/d26ae6f1-c04c-42bb-b33d-448650a53617)

## Selenium Suite
• Selenium IDE, a Firefox and Chrome add-on that you can only use in creating relatively simple test cases and test suites.
• Selenium Remote Control, also known as Selenium 1, which is the first Selenium 
tool that allowed users to use programming languages in creating complex tests.
• WebDriver, the newer breakthrough that allows your test scripts to communicate directly to the browser.
• Selenium Grid is also a tool that is used to execute parallel tests across different browsers and operating systems remotely.
• Selenium RC and WebDriver was merged to form Selenium 2.

[⬆ Back to Top](#index)

## Webdriver
Selenium WebDriver is an open-source automation tool for web applications. It allows testers to simulate user interactions like clicking, typing, and navigating pages across different browsers (Chrome, Firefox, Edge, etc.). WebDriver supports multiple programming languages (Java, Python, C#, etc.) and integrates with testing frameworks like TestNG and JUnit. It is widely used for functional and regression testing.

It's a Java Interface(Blue print of class), It is an API

![New Project](https://github.com/user-attachments/assets/1d0b0b10-5c57-48ba-aef7-a16ce5804c74)

## Steps to Create a Maven Project for Selenium Testing in Eclipse
1. Install Prerequisites
- Ensure Java JDK and Eclipse IDE are installed.
- Install Maven (or use Eclipse’s built-in Maven).
- Install Selenium WebDriver JARs (later added via dependencies).

2. Create a Maven Project
- Open Eclipse → Go to File → New → Maven Project.
- Select Create a simple project and click Next.
- Enter Group Id (e.g., com.selenium.test).
- Enter Artifact Id (e.g., SeleniumMavenProject).
- Click Finish to create the project.

3. Add Selenium Dependencies
- Open pom.xml and add the following dependencies inside <dependencies>:
```java
<dependencies>
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>latest_version</version>
    </dependency>

    <dependency>
        <groupId>org.testng</groupId>
        <artifactId>testng</artifactId>
        <version>latest_version</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```
- Save the file and let Maven download dependencies.

4. Create a Test Class
- In src/test/java, create a new package (com.test).
- Inside the package, create a Java class (TestGoogle.java).

5. Write a Selenium Test Script
- Example TestNG Selenium script:
```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.Test;

public class TestGoogle {
    @Test
    public void openGoogle() {
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.google.com");
        System.out.println("Google opened successfully!");
        driver.quit();
    }
}
```
6. Run the Test
- Right-click on the test class → Run As → TestNG Test.
- - Verify that Chrome opens and loads Google.

7. (Optional) Configure testng.xml for Multiple Tests
- Create testng.xml in the project root:
```java
<suite name="TestSuite">
    <test name="GoogleTest">
        <classes>
            <class name="com.test.TestGoogle"/>
        </classes>
    </test>
</suite>
```
[⬆ Back to Top](#index)

## Web Elements & Locators in Selenium  

### 📌 What is a Web Element?  
A **Web Element** is any HTML component on a webpage, such as:  
- Buttons  
- Text fields  
- Links  
- Checkboxes  
- Dropdowns  

To interact with these elements, Selenium needs a way to **find** them. That’s where **Locators** come in!  

---

### 🔍 Locators in Selenium  
Locators help Selenium **identify** web elements on a page. Below are the commonly used locators:  

### 1️⃣ **ID**  
- Fastest and most reliable (if unique).  
- Example:  
```java
  driver.findElement(By.id("username")).sendKeys("admin");
```
### 2️⃣ **Name**  
Useful when elements have unique name attributes.

```java
driver.findElement(By.name("email")).sendKeys("test@example.com");
 ```
### 3️⃣ **Class Name**
Selects elements based on their class attribute.

```java
driver.findElement(By.className("login-btn")).click();
 ```
### 4️⃣ Tag Name
Finds elements by HTML tag (<input>, <a>, <button>).

```java
driver.findElement(By.tagName("button")).click();
 ```
### 5️⃣ Link Text
Finds hyperlinks (<a>) using the exact link text.

```java
driver.findElement(By.linkText("Forgot Password?")).click();
 ```
### 6️⃣ Partial Link Text
Similar to Link Text but works with partial text.

```java
driver.findElement(By.partialLinkText("Forgot")).click();
 ```
### 7️⃣ CSS Selector
Powerful and flexible locator method.

```java
driver.findElement(By.cssSelector("input[name='q']")).sendKeys("Selenium");
 ```
### 8️⃣ XPath
Most powerful locator, used when others fail.

1. Example (Absolute XPath):
```java
driver.findElement(By.xpath("/html/body/div/input")).click();
 ```
2. Example (Relative XPath):
```java
driver.findElement(By.xpath("//input[@name='q']")).sendKeys("Selenium");
 ```

### Conclusion
Choosing the right locator is crucial for test stability and performance.
- Use ID and Name when available (fastest).
- Use XPath and CSS Selectors when needed (more flexible but slower).
- Avoid absolute XPath as it may break with UI changes.

[⬆ Back to Top](#index)

## Amazon Product Search Automation

### ✅ Test Cases for Amazon Product Search  

| **TC ID**  | **Test Case**                         | **Steps**                                       | **Expected Result**                               |
|------------|--------------------------------------|------------------------------------------------|------------------------------------------------|
| **TC_001** | Verify search bar functionality     | Enter "iPhone 15" in search bar & click search | Results should display **"iPhone 15"**         |
| **TC_002** | Check auto-suggestions              | Type "Laptop" in search bar                    | Suggestions should appear                      |
| **TC_003** | Search for invalid product          | Enter "xyz123randomproduct"                    | "No results found" message                     |
| **TC_004** | Search using filters                | Select "Electronics" & search "Smartphone"     | Results should be from **"Electronics"** category |
| **TC_005** | Verify search performance           | Search "Gaming Laptop"                         | Results should load within **3-5 sec**        |

---

### 🔍 Web Elements & Locators  

Selenium uses **locators** to find web elements on a page.  

| **Locator**          | **Example**                                             |
|----------------------|---------------------------------------------------------|
| **ID**              | `driver.findElement(By.id("searchBox"))`                 |
| **Name**            | `driver.findElement(By.name("q"))`                       |
| **Class Name**      | `driver.findElement(By.className("btn-search"))`         |
| **Tag Name**        | `driver.findElement(By.tagName("button"))`               |
| **Link Text**       | `driver.findElement(By.linkText("Click Here"))`          |
| **Partial Link Text** | `driver.findElement(By.partialLinkText("Click"))`      |
| **CSS Selector**    | `driver.findElement(By.cssSelector("input[name='q']"))`  |
| **XPath**          | `driver.findElement(By.xpath("//input[@name='q']"))`      |

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterClass;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;

public class AmazonSearchTest {
    WebDriver driver;

    @BeforeClass
    public void setup() {
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("https://www.amazon.com/");
    }

    @Test
    public void testProductSearch() {
        WebElement searchBox = driver.findElement(By.id("twotabsearchtextbox"));
        searchBox.sendKeys("iPhone 15");
        driver.findElement(By.id("nav-search-submit-button")).click();
        WebElement searchResult = driver.findElement(By.xpath("//span[contains(text(),'iPhone 15')]"));
        Assert.assertTrue(searchResult.isDisplayed(), "Search result validation failed!");
    }

    @AfterClass
    public void teardown() {
        driver.quit();
    }
}
```

### 📝 Short Notes on Selenium Test
✔ @BeforeClass - Initializes WebDriver, maximizes browser, and opens Amazon.

✔ @Test -
- Locates search box and enters "iPhone 15".
- Clicks search button.
- Verifies search results contain "iPhone 15".

✔ @AfterClass - Closes the browser after test execution.

### 🔹 Key Takeaways
✅ Uses TestNG for structured test execution <br>
✅ Uses By.id() and By.xpath() for locators <br>
✅ Uses Assertions to validate search results <br>
✅ Ensures browser handling with @BeforeClass & @AfterClass <br>

## Reference
- Edureka
- SDET-QA
- College Notes

## Author 
- Vaibhav R. Kale - QA Tester<br>
[Code360](https://www.naukri.com/code360/profile/CoderVK) &nbsp; &nbsp;
[LinkedIn](https://www.linkedin.com/in/vaibhav-kale)
