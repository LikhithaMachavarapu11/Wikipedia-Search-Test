
# 🌐 Wikipedia Search Test (Automation Project)

# 🧩 Technologies Used

- **Programming Language:** Java
- **Automation Tool:** Selenium WebDriver
- **IDE Used:** IntelliJ IDEA / VS code
- **Browser Tested:** Google Chrome
  
---

# Prerequisites (what you need before running)   

# **1️⃣ Installing IDE - Intellij, VS code**  
1.Install IntelliJ on Windows - Install version 2018.3.6 version for Windows 64 bit.  
2.Installing Java (JDK) - Install 11.0.2(build 11.0.2+9) version for Windows 64 bit.    
**Environment variables:**  
1.User Variables - click on new and give variable name as JAVA_HOME and variable value name is paste the url of java 11.0.2 folder URL  
2.System variables - select path in variables and click on new then paste bin folder URL

# **2️⃣ Chrome Driver installation**
Download chromedriver based on chrome version

# **3️⃣ Creating a new Project in Intellij**   
Java JDK installed (11 usually). In IntelliJ: File → Project Structure → SDKs — make sure JDK is configured.  
1.Maven java project  
2.version: java 11  
3.click on "Next"  
4.Group Id: org.example  
5.Artifact Id: sample-Test  
6.click on "Next"  
7.project name: sampleTest  
8.project location: C:\Users\likhi\IdeaProjects\sampleTest  
9.click on "Finish"   

**sample-Test.xml**  -  In sample-Test paste dependency section and refresh in maven.   
**Maven** -  “Maven is a build and dependency management tool for Java. It helps download all required libraries automatically using the pom.xml file and makes building and running the project easy.”                  
**Dependency Section**   
<dependencies>  
<dependency>  
  <groupId>org.seleniumhq.selenium</groupId>  
  <artifactId>selenium-java</artifactId>  
  <version>4.9.1</version>  
</dependency>  
</dependencies>
  
---

# ⚙️ How It Works    

# **1️⃣ Import Statements**  
import org.openqa.selenium.WebDriver;   
import org.openqa.selenium.chrome.ChromeDriver;  
import org.openqa.selenium.WebElement;  
import org.openqa.selenium.By;  
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.time.Duration;
import java.util.List;   

**Terms**  
- **WebDriver:** Used by Selenium to talk to any browser (Chrome, Firefox, Edge, etc.)  or Controls the browser
- **ChromeDriver:**	Used by Selenium to talk only to Chrome  or Connects Selenium to Chrome
- **WebElement:**	Represents a single element on a web page (like a button or paragraph).  or Represents a webpage item
- **By:**	Helps find elements (using CSS selector, ID, etc.). or Locator to find elements
- **ExpectedConditions:** Wait rules
- **WebDriverWait:** Makes Selenium wait
- **Duration:** Waiting time setting
- **List:** Stores many elements
 
# **2️⃣ Class and Main Method**  
public class WikiSearchTest {  
public static void main(String[] args) {  
}  
}
 
**Explanation:** Every Java program needs a class and a main method to run. main() is where execution starts. Think of it as the “entry door” for your program.

# **3️⃣ Set ChromeDriver Path**   
System.setProperty("webdriver.chrome.driver","C:\\Users\\likhi\\Downloads\\chromedriver-win64 (1)\\chromedriver-win64\\chromedriver.exe");    

**terms**   
- **System:**	A built-in Java class that lets you talk to your computer’s system settings.  
- **.setProperty():**	A method (function) used to set or define a “system property” — basically, a key and a value.   
- **"webdriver.chrome.driver":**	This is the key name — it tells Selenium, “Hey, this setting is about the ChromeDriver.”    
- **"C:\\Users\\likhi\\Downloads\\chromedriver-win64 (1)\\chromedriver-win64\\chromedriver.exe":**	This is the exact file path where ChromeDriver is saved on your computer.

**🔹Explanation:** This line tells Selenium where the ChromeDriver file is located on your computer. Selenium needs that file to open and control the Chrome browser for automation. Selenium doesn’t directly talk to Chrome — it communicates through ChromeDriver (a bridge). So before launching Chrome, you must tell Selenium where that driver is located.

**💡 Simple Example:** Imagine you’re the manager (Selenium) who wants to drive a car (Chrome). But you can’t start the car directly — you need the key (ChromeDriver). This line says: “Hey Selenium, your key (ChromeDriver.exe) is kept here — use it to start the car.”

# **4️⃣ Launch Chrome Browser**
WebDriver driver = new ChromeDriver();

**terms**  
- **WebDriver:** Used by Selenium to talk to any browser (Chrome, Firefox, Edge, etc.)   
- **ChromeDriver:**	Used by Selenium to talk only to Chrome

**Explanation:** Creates an object called driver that opens and controls Chrome. You’ll use driver to do things like open a website, click buttons, or read text.

**💡 Example:**  Think of driver like a remote control that can open websites and perform actions automatically.
- 🧠 Selenium = brain (it gives instructions)
- 🚗 WebDriver = hands (it performs actions in any browser)

# **5️⃣ Open the Website**     
driver.get("https://qawikisearch.ccbp.tech/");

**Explanation:** Tells Chrome to go to the given URL. 

**💡 Real Example:**  If you type that URL in Chrome manually, it opens the same page. Selenium is just doing it automatically.

# 6️⃣ Find the input field with id searchInput   
// Find the input field with id searchInput- use (Relative) XPath Locator.  
WebElement usernameElement = driver.findElement(By.xpath("//input[@id='searchInput']"));

**Explanation:** This code finds the text box with id="searchInput" on the web page and stores it in a variable called usernameElement.

**terms**  
- **WebElement:** This is a data type (class) in Selenium that represents a single element (like a button, paragraph, link, input box, etc.) on a web page.    
- **usernameElement:**  This is just a variable name — you can name it anything (like userNameElement or textElement).  
- **driver:** Your browser controller (created earlier by WebDriver driver = new ChromeDriver();).  
- **.findElement():**  A Selenium method used to find a single element on the web page.
- ****By.xpath("//input[@id='searchInput']"):**** By → means you’re using a locator to find something on the page. xpath → is one of the ways (methods) Selenium uses to locate elements in the HTML structure of a web page. So, By.xpath(...) means “find the element using its XPath address.” // → means “search anywhere in the page.” input → means look for an <input> tag (usually a textbox). [@id='searchInput'] → means the input should have an id attribute equal to searchInput.        


**💡 Explanation:**  This code finds the text box with id="searchInput" on the web page and stores it in a variable called usernameElement.

# 7️⃣ Enter the text HTML in the input field  
// Enter the text HTML in the input field.  
  usernameElement.sendKeys("HTML");

**Explanation:** It  tells Selenium to type the word “HTML” into the input box on the web page automatically.

# 8️⃣ Find the 'Search' with class name search-button
// Find the 'Search' with class name search-button - use (Relative) XPath Locator.
        WebElement searchButton = driver.findElement(By.xpath("//button[@class='search-button']"));

**Explanation:** finds the button on the web page whose class name is “search-button” and stores it in a variable called searchButton

# 9️⃣ Click the button 
// Click the button - use click() method.
        searchButton.click();

**Explanation:** tells Selenium to click the “Search” button on the web page automatically, just like you would click it with your mouse.


# **🔟 Find All Denomination Buttons:**  
//Wait until the search results (<div> elements) with class name result-item are loaded, for a maximum of 10 seconds  
//use visibilityOfElementLocated() method  
//use (Relative) XPath Locator   
// time duration 10 seconds   
WebDriverWait wait = new WebDriverWait(driver,Duration.ofSeconds(10));  

// wait until the elements are displayed    
wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//div[@class='result-item']")));  

//Find all the search results with class name result-item- use (Relative) XPath Locator.  
//Print " Results Found"  
//For example: 3 Results Found  
// verify the display of results on the page  

List<WebElement> results = driver.findElements(By.xpath("//div[@class='result-item']"));  
if (results.size()>0) {  
System.out.println( results.size() + " Results Found" );  
}

**Explanation:**
- WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10)); - This creates a wait timer that makes Selenium pause for up to 10 seconds. It’s useful when the web page takes time to load or show elements.
- wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//div[@class='result-item']"))); - This means Selenium will wait until it can see (i.e., the element is visible on the page) a <div> element with the class "result-item". As soon as the element appears, Selenium continues to the next step.
- List<WebElement> results = driver.findElements(By.xpath("//div[@class='result-item']")); - findElements() finds all matching elements on the page (not just the first one). Here, it searches for all <div> elements with the class "result-item". All those elements are stored in a list called results.
- if else - “Find all result items on the page, count them, and print how many results were found.”
  

# **1️⃣1️⃣ Close the Browser**
driver.quit();

**Explanation:** Closes the browser window.
   
---

# # # 🧾 Sample Test Flow

# 1️⃣ Open Chrome Browser automatically by using Selenium   
import org.openqa.selenium.WebDriver;  
import org.openqa.selenium.chrome.ChromeDriver;  
public class WikiSearchTest {  
public static void main(String[] args) {

        // set the path to the Chrome Driver executable
       System.setProperty("webdriver.chrome.driver","C:\\Users\\likhi\\Downloads\\chromedriver-win64 (1)\\chromedriver-win64\\chromedriver.exe");

        // Launch the Chrome browser
        WebDriver driver = new ChromeDriver();
    }
}  
 
# **Output:**     
Output in Chrome   
<img width="1293" height="988" alt="first step" src="https://github.com/user-attachments/assets/b7c2b588-d17d-4eb6-bcc6-d464473d82f4" />  

# 2️⃣ Navigate to the URL   
 // Navigate to WikiSearchTest Page
        driver.get("https://qawikisearch.ccbp.tech/");
  
# **Output:**    
Output in Chrome   
<img width="1285" height="982" alt="image" src="https://github.com/user-attachments/assets/7baab79b-f432-4ded-a576-d726b6e61898" />


# 3️⃣ Find the input field   
// Find the input field with id searchInput- use (Relative) XPath Locator.  
WebElement usernameElement = driver.findElement(By.xpath("//input[@id='searchInput']"));


# **Output:**  
Output in Chrome    
<img width="1285" height="982" alt="image" src="https://github.com/user-attachments/assets/7baab79b-f432-4ded-a576-d726b6e61898" />

# 4️⃣ Enter the text HTML in the input field
// Enter the text HTML in the input field.  
    usernameElement.sendKeys("HTML");

# **Output:**     
Output in Chrome  
<img width="1288" height="988" alt="image" src="https://github.com/user-attachments/assets/bdc668ea-3dc4-48f0-9294-d0100d9f6dcd" />
   

# 5️⃣ Find and click the "Search" button 
// Find the 'Search' with class name search-button - use (Relative) XPath Locator.  
WebElement searchButton = driver.findElement(By.xpath("//button[@class='search-button']"));  
// Click the button - use click() method.   
searchButton.click();


# **Output:**
Output in Chrome
<img width="1276" height="989" alt="image" src="https://github.com/user-attachments/assets/d64e2866-bca6-4872-b996-8aead9acbb87" />


# 6️⃣ Verify the balance amount matches the expected amount 2000  
//Wait until the search results (<div> elements) with class name result-item are loaded, for a maximum of 10 seconds  
//use visibilityOfElementLocated() method  
//use (Relative) XPath Locator  
// time duration 10 seconds  
WebDriverWait wait = new WebDriverWait(driver,Duration.ofSeconds(10));  
// wait until the elements are displayed  
wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//div[@class='result-item']")));
       
# **Output:**   
Output in Chrome   
<img width="1276" height="989" alt="image" src="https://github.com/user-attachments/assets/d64e2866-bca6-4872-b996-8aead9acbb87" />


# 7️⃣ Find all the search results  
//Find all the search results with class name result-item- use (Relative) XPath Locator.  
//Print " Results Found"  
//For example: 3 Results Found   

// verify the display of results on the page  
List<WebElement> results = driver.findElements(By.xpath("//div[@class='result-item']"));   
if (results.size()>0) {  
System.out.println( results.size() + " Results Found" );  
}

# **Output:**   
Output in Chrome
<img width="1276" height="989" alt="Screenshot 2025-10-13 212900" src="https://github.com/user-attachments/assets/353c371c-be6d-442d-a3e7-6796634e11d7" />   
Output in Intellij
<img width="649" height="188" alt="image" src="https://github.com/user-attachments/assets/1627a3b8-7f38-481b-a80f-a6a03acc20e1" />


# 8️⃣ Close the browser
// Close the browser window.  
driver.quit();       

**Explanation:** 
closes the Chrome browser automatically and stops ChromeDriver
  
---


## 🖼️ Final Output of the Project   
<img width="649" height="188" alt="image" src="https://github.com/user-attachments/assets/1627a3b8-7f38-481b-a80f-a6a03acc20e1" />

<br><br>

---

