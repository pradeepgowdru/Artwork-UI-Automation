# Bizongo-Artwork-UI-Automation
<p align="center">
<img src="https://user-images.githubusercontent.com/16290315/55854379-1b18d880-5b82-11e9-9a04-2ec363bb56b8.png" height="400" align="middle">
</p>
<p align="center">
<b>A set of Behavioural tests that can be run against our UI.</b>
</p>


## Introduction
We are making use of [Cucumber](https://cucumber.io/) to write our UI Tests in Plain English. We will be testing and validating UI using [Selenium Webdriver](https://www.seleniumhq.org/projects/webdriver/). Selenium Webdriver helps to drive a browser natively as a user would either locally or on a remote machine using the Selenium Server it marks a leap forward in terms of browser automation.

## Feature Files
A Feature File is an entry point to the Cucumber tests. This is a file where you will describe your tests in Descriptive language (Like English). It is an essential part of Cucumber, as it serves as an automation test script. A feature file can contain a scenario or can contain many scenarios in a single feature file but it usually contains a list of scenarios. Feature files of our project will be present in [features](https://github.com/Bizongo/UI-Automation/tree/master/Features) folder.

## Examples of Writing Test in Feature File
These examples are taken from the test 
* [Features Example 1](https://github.com/Bizongo/UI-Automation/blob/master/Features/LeadPlus/003_Deals/Deals.feature)
* [Features Example 2](https://github.com/Bizongo/UI-Automation/blob/master/Features/LeadPlus/002_Deals/DealSuppliers.feature)

#### Examples:

```gherkin
@bizongo @high
Feature: To Test the Deal Products Module Functionality for Lead Plus

  Background: User opens the Create Deal Modal
    And You Click on "Plus":"icon" on Header
    And You Click on "Create Deal":"popover" on Header
    And Fill the "Amazon" Details on Create Deal Modal
    And You Click on "Submit":"button" on Create Deal Modal
    And Fill the "Normal Deal" "Amazon" Details on Create Deal
    And You Click on "Submit":"button" on Create Deal

  @bizongo @high
  Scenario Outline: Verify user can Request for quotes from Products page
    And You Click on "Products":"link" on Deal Navigation Bar
    And You Click on "Link Product":"button" on Deal Products Page
    And You Click on "Add New Product":"button" on Search Products Page
    And You Click on "Rating":"button" on Add New Product Modal
    And You enter the Product specifications on Add New Product Modal
    And You Click on "Save":"button" on Add New Product Modal
    And You Click on Okay button on Add New Product Modal
    And You Click on "Notification":"popup" on Deal Products Page
    And You Click on "Request Quote":"button" on Deal Products Page
    And You enter the "Assign To Pg":"textbox" on "<Request Quote>" Modal
    And You Click on "Assign To Pg":"dropdown" on Request Quote Modal
    And You enter the "Target Price":"textbox" on "<Request Quote>" Modal
    And You enter the "Message":"textarea" on "<Request Quote>" Modal
    And You Click on "Request":"button" on Request Quote Modal
    Then Verify whether "QUOTES REQUESTED":"text" is displayed on DealDetails Page
    Examples:
      | Request Quote |
      | First Quote   |
 ```

In above example, the keyword **Feature** stands for the Feature that we are testing, in this case To Test the Deal Products Module Functionality for Lead Plus.

@bizongo is a **tag** which we will use in Hook class to set the BaseUrl and @high is a **tag** to specify while running tests that we want to run tests of high priority ( Nothing much to worry about it )

**Background** Keyword is used to run the set of steps before running the actual scenario.

**Scenario Outline and Examples** Keyword stands for the name of the scenario we will be testing, in this case Verify user can Request for quotes from Products page. If we are using Scenario Outline then we will have to pass the Data using Examples. If we have scenarios that vary only on the data sets (input data sets or output data sets), then scenario outlines are very helpful as they reduce the verbosity. Scenario Outline and Examples go hand in hand. The <> contains the parameter which is substituted from the table for each row when the scenario is run. So we can have the data-driven scenarios done through Scenario Outline. In this case we are passing the name of data set i.e "First Quote" present in the [Json File](https://github.com/Bizongo/UI-Automation/blob/master/resources/TestDataResources/leadplus/requestquote.json)
                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
**And** is the keyword using which we will add the steps or conditions.

**Then** is the keyword using which we will use to verify the expected result of the scenario, in this case Verify whether "QUOTES REQUESTED":"text" is displayed on DealDetails Page.

##### Now let's breakdown the steps mentioned above:
```gherkin
   And You Click on "Plus":"icon" on Header
```

* In the above case we are clicking on an element:
    * Here **Plus** is the name of the element we click on.
    * **icon** is the type of the element on which we will click on.

```gherkin
   And You enter the "Target Price":"textbox" on "<Request Quote>" Modal
```

* In the above case we will enter value in an element:
    * Here **Target Price** is the name of the element in which we will enter value.
    * **textbox** is the type of the element in which we will enter value.

```gherkin
   And You Select "First Value" from "Price Type":"dropdown" on Deal Suppliers Page
```

* In the above case we will select value from dropdown:
    * Here **First Value** is the first value from dropdown that we will select.
    * Here **Price Type** is the name of the dropdown element.
    * **dropdown** is the type of the element.

```gherkin
   Then Verify whether "QUOTES REQUESTED":"text" is displayed on DealDetails Page
```

* In the above case we will verify whether a particular text is displayed on the page:
    * Here **QUOTES REQUESTED** is the text that need to be displayed on the page.
    * Here **text** is the type of the element.
    
```gherkin
   Then Verify whether "Master Sku Id":"text" is present on Deal Products Page
```

* In the above case we will verify whether a particular text is displayed on the page:
    * Here **QUOTES REQUESTED** is the text that needs to be present on the page.
    * Here **text** is the type of the element.

```gherkin
   Then Verify whether "Quotation for the Products you Inquired" text is present in Pdf
```

* In the above case we will verify whether a particular text is displayed on the page:
    * Here **Quotation for the Products you Inquired** is the text that needs to be present in the PDF.
   
```gherkin
   And You navigate to previous page from Quotation Details Page
```  
   * Navigate to the previous page from Particular Page

```gherkin
   And You Click on "Notification":"popup" on Request Quote Modal if Present
```  
  * Here **Notification** is the name of the element.
  * Here **popup** is the type of the element.
These will be used for random elements which might be present or not present.

```gherkin
   And Then Verify whether background color of "Quotes":"row" is "Iron" on Deal Quotes Page
```  
  * Here **Quotes** is the name of the element.
  * Here **row** is the type of the element.
  * Here **Iron** should be the color of the element.

```gherkin
   And You Refresh the DealDetails Page
```  
  If you want to refresh the particular page
  
```gherkin
   Then Verify whether "EXTEND RFQ":"button" is not displayed on Deal Suppliers Page
```  
  * Here **EXTEND RFQ** is the name of the element.
  * Here **button** is the type of the element.
  
```gherkin
   Then Verify whether "Dispatch Time":"text" is same as input on Quotes Details Modal
```  
   * Here **Dispatch Time** is the element .
   * Here **text** is the type of the element.
   
   It should be same as the value you entered on some other page of your choice based on the test.
 
```gherkin
   And You Select 2 Suppliers on Deal Suppliers Page
```  
   * Here **2** is the numbers of elements you want to select.
   
```gherkin
   And Fill the "<Prospect>" Details
```  
   * Here **<Prospect>** is the name of the json object that will be passed via examples.

It will be used to enter a set of data in UI like forms.

```gherkin
   And Fill the "Amazon" Details on Create Deal Modal
```  
   * Here **Amazon** is the name of the json object. It should be used in background section.



## Prerequisites
  * JDK 11+
  * Maven
  
## Running tests
 * To run the tests locally following are the steps:
   * Clone the repository : git@github.com:Bizongo/Artwork-UI-Automation.git
   * Traverse to the Repo folder and run following commands:
   * cd /Artwork-UI-Automation/resources/runnerscript
   * sh test_script.sh Artworks https://artwork.qa4.indopus.in Chrome - Example
   * Once the script is finished, we can find the report at /Artwork-UI-Automation/target/cucumber-report-html/cucumber-html-reports/overview-features.html
   * Logs will be displayed on Console as well as log folder with timestamp will be present in project.
   

 
