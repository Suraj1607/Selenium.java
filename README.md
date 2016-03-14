# Selenium.java
Selenium files

package mypackage;
import org.testng.annotations.Test;
import org.testng.annotations.Test;
import org.testng.annotations.Test;
import org.testng.annotations.Test;
import org.testng.annotations.Test;
import java.util.List;
import java.util.concurrent.TimeUnit;
import junit.framework.Assert;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.interactions.Action;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.annotations.Test;
import org.openqa.selenium.*;
 
 

public class NewTest
{
WebDriver driver=new FirefoxDriver();

 
@Test(enabled=false)//Login
 
 public void f() throws InterruptedException
 {
WebDriver driver=new FirefoxDriver();
driver.get("http://automationpractice.com");
driver.manage().window().maximize();
 
Buttonclick(driver,"//a[@class='login']");
 
enter(driver,"//input[@id='email_create'and @name='email_create']","suraj@hexaware2.com");
Buttonclick(driver,"//button[@id='SubmitCreate']");
 
driver.manage().timeouts().implicitlyWait(5000, TimeUnit.MILLISECONDS);
 
Buttonclick(driver,"//input[@id='id_gender1']");
 
enter(driver,"//input[@id='customer_firstname']","Suraj");
 
enter(driver,"//input[@id='customer_lastname']","behera");
 
enter(driver,"//input[@id='passwd']","behera");
 
WebElement path=driver.findElement(By.xpath("//div[@id='uniform-days']/select"));
NewTest.drop(path,"1  ");
WebElement path2 = driver.findElement(By.xpath("//div[@id='uniform-months']/select"));
drop(path2,"January ");
WebElement path3=driver.findElement(By.xpath("//div[@id='uniform-years']/select"));
drop(path3,"2016  ");
Buttonclick(driver,"//input[@id='optin']");
clear(driver,"//input[@id='firstname']");
enter(driver,"//input[@id='firstname']","Suraj");
clear(driver,"//input[@id='lastname']");
enter(driver,"//input[@id='lastname']","behera");
enter(driver,"//input[@id='address1']","Baripada");
enter(driver,"//input[@id='city']","Baripada");
WebElement path4=driver.findElement(By.xpath("//select[@id='id_state']"));
drop(path4,"Alaska");
enter(driver,"//input[@id='postcode']","12345");
WebElement path5=driver.findElement(By.xpath("//select[@id='id_country']"));
drop(path5,"United States");
enter(driver,"//input[@id='phone_mobile']","9861353859");
Buttonclick(driver,"//button[@id='submitAccount']");
 
 }
 public void Buttonclick(WebDriver driver,String path)
 {
 WebElement click;
 click=driver.findElement(By.xpath(path));
 click.click();
 }
 
 public void enter(WebDriver driver,String path,String text)
 {
 WebElement ent;
 ent=driver.findElement(By.xpath(path));
 ent.sendKeys(text);
 }
 
 public static boolean drop(WebElement path,String sel)
 {
 
 
 Select select = new Select(path);
 
 List<WebElement> el = select.getOptions();
 
 System.out.println(el.size());
 
 
 for(int i=0;i<el.size();i++)
 {
 
 System.out.println("The elements are"+ el.get(i).getAttribute("value"));
 
 }
 
 select.selectByVisibleText(sel);
 
 return true;
 
 
 }
 
 public void clear(WebDriver driver,String path)
 {
 WebElement cl=driver.findElement(By.xpath(path));
 cl.clear();    
 }
 
 
 @Test(enabled=false) //selecting a product
 public void commonaction()
 {
 WebDriver driver=new FirefoxDriver();
 driver.navigate().to("http://automationpractice.com");
 //selectprod(driver);
 
 
 }
 public void selectprod(WebDriver driver,String path)
 {
Actions a=new Actions(driver);
 
WebDriverWait wait=new WebDriverWait(driver,10);
WebElement element=wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//ul[@id='homefeatured']/li[7]/div/div/div/a/img[@class='replace-2x img-responsive']")));
 
a.moveToElement(element).build().perform();
driver.findElement(By.xpath("//ul[@id='homefeatured']/li[7]/div/div[2]/div[2]/a/span")).click();
 
 }
 @Test(enabled=false)//TS_ID_76
 
 public void compare() throws InterruptedException 
 {
  
  driver.get("http://automationpractice.com/index.php");
  driver.manage().window().maximize();
  
  Actions a=new Actions(driver);
  WebDriverWait wait=new WebDriverWait(driver,10);
  
  
  WebElement element=wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//div[@id='block_top_menu']/ul/li[1]/a")));
  a.moveToElement(element).build().perform();
  driver.findElement(By.xpath("//div[@id='block_top_menu']/ul/li/ul/li[2]/ul/li[1]/a")).click();
  
  //click on compare
  
  Actions b = new Actions(driver);
  
  WebElement element2=driver.findElement(By.xpath("//ul[@class='product_list grid row']/li/div/div/div/a"));
  driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
  b.moveToElement(element2).build().perform();
  driver.findElement(By.xpath("//div[@class='row']/div[2]/ul/li/div/div[3]/div[2]/a")).click();
  Thread.sleep(5000);
  
  
 /* WebElement e=driver.findElement(By.xpath("//*[@id='center_column']/div[3]/div/form/button"));
  System.out.println("The Compare button is having the following no of items:"+e.getText());*/
  
  WebElement e=driver.findElement(By.xpath("//div[@id='center_column']/div[3]/div/form/input[1]"));
  System.out.println("The Compare button is having the following no of items:"+e.getAttribute("value"));
  
  Thread.sleep(3000);
  driver.findElement(By.xpath("//div[@id='center_column']/div[3]/div/form/button")).click();
  
  
 }
 @Test(enabled=false)//TS_ID_78
  public void delete()
  {
  
  WebDriverWait comparewait = new WebDriverWait(driver,5);
  comparewait.until(ExpectedConditions.presenceOfElementLocated(By.xpath("//a[@class = 'cmp_remove' and @title='Remove']")));
  WebElement e=driver.findElement(By.xpath("//a[@class = 'cmp_remove' and @title='Remove']"));
  System.out.println(e.getText());
  
  Assert.assertTrue("the delete button is unabled", e.isEnabled());
  
  e.click();
  driver.quit();
  }
 
 @Test(enabled=false)//TS_ID_79
 	public void sharefb()
 		{
	 		WebElement e = driver.findElement(By.xpath("//button[@class='btn btn-default btn-block btn-facebook']"));
	 		Assert.assertTrue("The Share with FB link is enabled", e.isEnabled());
	 		e.click();
	 			 			 
 		}
 	//button[@class='btn btn-default btn-block btn-facebook']
  
 @Test//TS_ID_65-Validate the search output with the specific search
 	public void search()
 		{
	 		driver.get("http://www.automationpractice.com");
	 		driver.manage().window().maximize();
	 		driver.findElement(By.xpath("//input[@id='search_query_top']")).sendKeys("dress");
	 		driver.findElement(By.xpath("//button[@name='submit_search']")).click();;
	 		driver.manage().timeouts().implicitlyWait(5000, TimeUnit.SECONDS);
	 		String e=driver.findElement(By.xpath("//div[@id='center_column']/h1/span[1]")).getText();
	 		System.out.println("The Searched element is of catagories"+e);	 
 		}
 @Test//TS_ID_66-Validate the Sort By Functionality with the available options. Verify the different outputs for each selection.
 	public void sort()
 		{
	 		WebElement path=driver.findElement(By.xpath("//select[@id='selectProductSort']"));
	 		Select select=new Select(path);
	 		List<WebElement> element=select.getOptions();
	 		
	 		for(int i=0;i<=element.size();i++)
	 		{
	 			select.selectByIndex(i+1);
	 			System.out.println("The filter condition used is:"+element.get(i).getText());
	 			
	 			//Assert.assertEquals(expected, actual);			
	 		}
	 	select.selectByVisibleText("Price: Lowest first");
	 	driver.manage().timeouts().implicitlyWait(5000,TimeUnit.SECONDS);
	 	
	 	for(int i=0;i<=element.size();i++)
	 		{
	 			if(element.get(i).getText().equalsIgnoreCase("Price: Lowest first"))
	 			{
	 				System.out.println("The sorting condition is fulfilled and is shorted by: "+element.get(i).getText());
	 			}
	 	
	 		}
 		}
}
  
  
 
