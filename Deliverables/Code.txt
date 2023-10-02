package paademo1;
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;
import org.testng.annotations.*;

public class paademo1  {
    ChromeDriver driver;
    @BeforeSuite
    public void browserSetup() {
        System.setProperty("webdriver.chrome.driver", "C:\\Users\\Shohel\\Desktop\\ProjectControl\\Driver\\chromedriver-win64\\chromedriver.exe");
        driver = new ChromeDriver();
        driver.get("https://www.amazon.com/");
    }

    @AfterSuite
    public void tearDown() {
        driver.quit();
    }

    @Test(priority = 1)
    public void runOnChrome() throws InterruptedException {

        WebElement dropDown = this.driver.findElement(By.id("searchDropdownBox"));
        Select selectObject = new Select(dropDown);
        selectObject.selectByVisibleText("Baby");
        driver.findElement(By.id("searchDropdownBox")).click();
        Thread.sleep(2000);
    }
    @Test(priority = 2)
    public void textOnChrome() throws InterruptedException {
        driver.findElement(By.id("twotabsearchtextbox")).click();
        WebElement inputBox = driver.findElement(By.id("twotabsearchtextbox"));
        inputBox.sendKeys("bag");
        Thread.sleep(2000);
        driver.findElement(By.id("nav-search-submit-button")).click();
        Thread.sleep(2000);
    }

}
