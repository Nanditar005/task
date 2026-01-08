# task
package sampleProject;

import static org.testng.Assert.assertEquals;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.annotations.Test;

public class Logintest extends BaseTest {

	@Test
	public void loginpage() throws InterruptedException {// Smoketest
		driver.get("https://the-internet.herokuapp.com/login");
		String actualTitle = driver.getTitle();
		String ExpectedTitle = "The Internet";
		System.out.println("Actual Title = " + actualTitle);
		assertEquals(actualTitle, ExpectedTitle, "Page title does not match the expeted one");

		WebElement Passwordfield = driver.findElement(By.name("password"));
		String actualType = Passwordfield.getAttribute("type");
		String expectedType = "password";
		System.out.println("Actual Type = " + actualType);
		assertEquals(actualType, expectedType, "password field is not as expected");

		String actualText = driver.findElement(By.tagName("h2")).getText();// failed test case
		String expectedText = "Login Page";
		System.out.println("Actual Text = " + actualText);
		assertEquals(actualText, expectedText, "text not begins with expected value");

		WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(05));// sanityTest
		WebElement usernamefield = wait.until(ExpectedConditions.visibilityOfElementLocated(By.name("username")));
		// driver.findElement(By.name("username")).sendKeys("tomsmith");
		usernamefield.sendKeys("tomsmith");
		WebElement passwordfield = driver.findElement(By.name("password"));
		passwordfield.sendKeys("SuperSecretPassword!");
		WebElement login = driver.findElement(By.className("radius"));
		login.click();
		System.out.println("Smoke and sanity tests are verified successfully");
	}

}
