# task
package Smoketest;
import java.time.Duration;

import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

public class Sampletest {
	static WebDriver driver;
	
	public static void main(String[] args) {
		
		WebDriver driver =new ChromeDriver();
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
		driver.get("https://the.internet.herokuapp.com/login");
		driver.findElement(By.id("username")).sendKeys("tomsmith");
		driver.findElement(By.id("password")).sendKeys("superSecretPassword!");
		
		String pass=driver.findElement(By.id("password")).getAttribute("type");
		
		if(pass.equals("password")) {
			System.out.println("masked");
		}
		else {
			System.out.println("notmasked");
		}
		
		String title=driver.getTitle();
		if(title.contains("The")) {
			System.out.println("pass");
		}
		driver.findElement(By.className("radius")).click();
		
		WebElement usernamefield =driver.findElement(By.name("username"));
		usernamefield.sendKeys("tomsmith");
		WebElement passwordfield = driver.findElement(By.name("password"));
		passwordfield.sendKeys("SuperSecretPassword!");
		WebElement login=driver.findElement(By.className("radius"));
		
		login.click();
	System.out.println("sanity test done successfully!");
	
	driver.quit();	
	}

	
	
	
}
