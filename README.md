# C#.NET Test Automation Recipes

- [NUnit](#NUnit)

- [MicrosoftUIAutomation](#MicrosoftUIAutomation)

- [Selenium](#Selenium) 

- [RestSharp](#RestSharp)

- [Playwright](#Playwright)

- [Appilotool](#Appilotool)

- [TestProject](#TestProject)

- [Moq](#Moq)

- [Specflow](#Specflow)

- [Appium](#Appium)

- [ExtentReports](#ExtentReports)

- [ApprovalTest](#ApprovalTest) 

- [WorkingWithFiles](#WorkingWithFiles)

- [Collections](#Collections)

- [LINQ](#LINQ)

- [ProxyMechanism](#ProxyMechanism)

- [WCF](#WCF)

- [SOAP](#SOAP)

- [HTTP](#HTTP)

- [TcpClient](#TcpClient)

- [ADODotNET](#ADODotNET)

- [XML](#XML) 

- [Serialization](#Serialization)

- [Json](#Json)

- [RegularExpression](#RegularExpression)

- [Reflection](#Reflection)

- [DotNetDiagnostics](#DotNetDiagnostics)

- [AsyncAndwait](#AsyncAndwait)

- [DateAndTimes](#DateAndTimes)

- [ConfigurableApplications](#ConfigurableApplications)

# C#.NET Test Automation Recipes

## NUnit 
### Learning Resource 
- [NUnit-Unit-Testing-Framework-Cheat-Sheet](https://www.automatetheplanet.com/wp-content/uploads/2018/06/NUnit-Unit-Testing-Framework-Cheat-Sheet.pdf)
- [Introduction to NUnit by Test Automation University](https://testautomationu.applitools.com/nunit-tutorial/)
### Installation
```
Install-Package NUnit
Install-Package NUnit.TestAdapter
Install-Package Microsoft.NET.Test.Sdk
```
### Test Execution Workfow
```csharp
using NUnit.Framework;
namespace NUnitUnitTests
{
	// A class that contains NUnit unit tests.	(Required)
	[TestFixture]
	public class NonBellatrixTests
	{
		[OneTimeSetUp]
		public void ClassInit()
		{
			// Executes once for the test class.(Optional)
		}
		[SetUp]
		public void TestInit()
		{
			// Runs before each test. (Optional)
		}
		[Test]
		public void TestMethod()
		{
		}
		[TearDown]
		public void TestCleanup()
		{
			// Runs after each test. (Optional)
		}
		[OneTimeTearDown]
		public void ClassCleanup()
		{
			// Runs once after all tests in this class are executed. (Optional)
			// Not guaranteed that it executes instantly after all tests from the class.
		}
	}
}
// A SetUpFixture outside of any namespace provides SetUp and TearDown for the entire assembly.
[SetUpFixture]
public class MySetUpClass
{
	[OneTimeSetUp]
	public void RunBeforeAnyTests()
	{
		// Executes once before the test run.(Optional)
	}
	[OneTimeTearDown]
	public void RunAfterAnyTests()
	{
		// Executes once after the test run.(Optional)
	}
}
```
### Assertions – Constraint Model
```csharp
Assert.AreEqual(28, _actualFuel); // Tests whether the specified values are equal.
Assert.AreNotEqual(28, _actualFuel); // Tests whether the specified values are unequal. Same as AreEqual for numeric values.
Assert.AreSame(_expectedRocket, _actualRocket); // Tests whether the specified objects both refer to the same object
Assert.AreNotSame(_expectedRocket, _actualRocket); // Tests whether the specified objects refer to different objects
Assert.IsTrue(_isThereEnoughFuel); // Tests whether the specified condition is true
Assert.IsFalse(_isThereEnoughFuel); // Tests whether the specified condition is false
Assert.IsNull(_actualRocket); // Tests whether the specified object is null
Assert.IsNotNull(_actualRocket); // Tests whether the specified object is non-null
Assert.IsInstanceOf(_actualRocket, typeof(Falcon9Rocket)); // Tests whether the specified object is an instance of the expected type
Assert.IsNotInstanceOf(_actualRocket, typeof(Falcon9Rocket)); // Tests whether the specified object is not an instance of type
StringAssert.AreEqualIgnoringCase(_expectedBellatrixTitle, "Bellatrix"); // Tests whether the specified strings are equal ignoring their casing
StringAssert.Contains(_expectedBellatrixTitle, "Bellatrix"); // Tests whether the specified string contains the specified substring
StringAssert.DoesNotContain(_expectedBellatrixTitle, "Bellatrix"); // Tests whether the specified string doesn't contain the specified substring
StringAssert.StartsWith(_expectedBellatrixTitle, "Bellatrix"); // Tests whether the specified string begins with the specified substring
StringAssert.StartsWith(_expectedBellatrixTitle, "Bellatrix"); // Tests whether the specified string begins with the specified substring
StringAssert.IsMatch("(281)388-0388", @"(?d{3})?-? *d{3}-? *-?d{4}"); // Tests whether the specified string matches a regular expression
StringAssert.DoesNotMatch("281)388-0388", @"(?d{3})?-? *d{3}-? *-?d{4}"); // Tests whether the specified string does not match a regular expression
CollectionAssert.AreEqual(_expectedRockets, _actualRockets); // Tests whether the specified collections have the same elements in the same order and quantity.
CollectionAssert.AreNotEqual(_expectedRockets, _actualRockets); // Tests whether the specified collections does not have the same elements or
the elements are in a different order and quantity.
CollectionAssert.AreEquivalent(_expectedRockets, _actualRockets); // Tests whether two collections contain the same elements.
CollectionAssert.AreNotEquivalent(_expectedRockets, _actualRockets); // Tests whether two collections contain different elements.
CollectionAssert.AllItemsAreInstancesOfType(_expectedRockets, _actualRockets); // Tests whether all elements in the specified collection are
instances of the expected type
CollectionAssert.AllItemsAreNotNull(_expectedRockets); // Tests whether all items in the specified collection are non-null
CollectionAssert.AllItemsAreUnique(_expectedRockets); // Tests whether all items in the specified collection are unique
CollectionAssert.Contains(_actualRockets, falcon9); // Tests whether the specified collection contains the specified element
CollectionAssert.DoesNotContain(_actualRockets, falcon9); // Tests whether the specified collection does not contain the specified element
CollectionAssert.IsSubsetOf(_expectedRockets, _actualRockets); // Tests whether one collection is a subset of another collection
CollectionAssert.IsNotSubsetOf(_expectedRockets, _actualRockets); // Tests whether one collection is not a subset of another collection
Assert.Throws<ArgumentNullException>(() => new Regex(null)); // Tests whether the code specified by delegate throws exact given exception of type T
```
### Author Attribute
```csharp
[TestFixture]
[Author("Joro Doev", "joro.doev@bellatrix.solutions")]
public class RocketFuelTests
{
	[Test]
	public void RocketFuelMeassuredCorrectly_When_Landing()
	{
		//...
	}
	[Test]
	[Author("Ivan Penchev")]
	public void RocketFuelMeassuredCorrectly_When_Flying()
	{
		//...
	}
}
```
## MicrosoftUIAutomation

## Selenium 
### Learning Resource 
- [Most Complete Selenium WebDriver C# Cheat Sheet](https://www.automatetheplanet.com/wp-content/uploads/2017/02/MostCompleteWebDriverCSharpCheetSheet.pdf)
- [Intro to Selenium WebDriver with .NET Core by Test Automation University](https://testautomationu.applitools.com/intro-to-selenium-webdriver-with-net-core/)
- [Web Element Locator Strategies](https://testautomationu.applitools.com/web-element-locator-strategies/)
- [Udemy Selenium WebDriver Masterclass with C#](https://www.udemy.com/course/selenium-with-c/)

## RestSharp

## Playwright

## Appilotool

## TestProject

## Moq

## Specflow

## Appium

## ExtentReports

## ApprovalTest 

## BCL 

### WorkingWithFiles

### Collections

### LINQ

### ProxyMechanism

### WCF

### SOAP

### HTTP

### TcpClient

### ADODotNET

### XML 

### Serialization

### Json

### RegularExpression

### Reflection

### DotNetDiagnostics

### AsyncAndwait

### DateAndTimes

### ConfigurableApplications
