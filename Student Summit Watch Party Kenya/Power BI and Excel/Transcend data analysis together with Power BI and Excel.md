# Enable compatibility with Excel

Completed100 XP

-   5 minutes

Using Microsoft Power BI is beneficial in situations when data exploration is best performed by using the interactive visual experience. Occasionally, you might want to explore your data by using PivotTables in Microsoft Excel.

The Microsoft Power BI suite of tools helps give organizations the freedom to use the analysis tool of their choice when it comes to analyzing information in the dataset. Not every user will have Power BI and Data Analysis Expressions (DAX) experience and might not want to learn a new tool.

Excel is still the most widely used analysis tool in the world, and it's the foundation for analytics for most departments. Microsoft recognizes the need to connect the new tools to that foundation. Enabling users to connect to your dataset in Excel will lead to better adoption and greater alignment to a _single version of the truth_ when everyone is using the same dataset to answer questions that are related to that part of the business.

# Connect Excel to Power BI datasets

Completed100 XP

-   15 minutes

Multiple ways are available for you to choose from when setting up a connection to Power BI datasets within Excel. The first two methods are geared more toward users who are not involved in the creation of the dataset. Additionally, these methods are more likely to be used after the dataset has been fully developed and deployed to production.

## Option 1: Insert PivotTable

-   In the **Insert** tab, select **PivotTable** > **From Power BI (xxxx*)**.

> [![Screenshot of Insert PivotTable from Power BI dataset.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/insert.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/insert.png#lightbox)

## Option 2: Get data connection

-   In the **Data** tab, select **Get Data** > **From Power BI** **(xxxx*)**.

> [![Screenshot of the Get Data menu with Power BI selected.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/get-data.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/get-data.png#lightbox)

*xxxx = Your organization's name

 Note

If the **From Power BI** button is not an option, be sure to install the most recent updates for Microsoft Office. If your system is fully updated, you might need to check with a Power BI admin to verify that the tenant settings and the certification setting for the datasets are enabled for users to connect in Excel.

The **Power BI Datasets** pane will appear on the right side of the screen, listing the possible datasets that you can connect to. Select the dataset that you want to connect to.

> [![Screenshot of PBI Datasets pane showing certifications.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/datasets.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/datasets.png#lightbox)

After you have selected the dataset that you want to use, a field list will appear that includes all possible fields from all tables that are included in the dataset, including the measures. This connection allows you to create PivotTables based off any field from the dataset. Use the same drag-and-drop process with the fields to create the desired format for your PivotTables.

After you have developed your PivotTable, this Excel file can be saved to OneDrive, OneDrive for Business, or SharePoint Online, which will allow you to consume, share, and collaborate in Microsoft Power BI service.

Power BI service includes two ways to help you keep Excel data updated:

-   Directly in the browser
    
-   In Power BI service
    

## Update directly in the browser

You can refresh the connected PivotTable by pasting the link to the workbook in your web browser. The link can be copied by using the **Share** button in the workbook or by going to **File** > **Info** > **Copy**. You can interact with the connected PivotTable in Excel for the web by dragging fields into the PivotTable area, all while keeping the data connected to the dataset. Make sure that you close any version of the workbook that is open in Excel desktop prior to changing the workbook in Excel for the web.

## Update in Power BI service

With the embedded Excel for the web view, you can interact with workbooks directly in a Power BI workspace. Also, you can work with connected PivotTables in a Power BI app by adding a published workbook to the app. 

 Note

If you get a **Query and Refresh** dialog message after opening a workbook with connected PivotTables, select **Yes** to continue because the Power BI dataset connection is already trusted.

# Dataset types and security

Completed100 XP

-   5 minutes

Modern Excel users can view promoted or certified datasets in Power BI and decide on the best dataset to use. Promoted datasets are endorsements from data modelers. Certified datasets are determined by the Power BI tenant admin, which is generally a higher endorsement from your organization. These labels ensure that a single version of the truth is used, regardless of the analysis tool.

[![Screenshot of the selection of a Power B I Data set for use in Excel.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/power-bi-datasets-in-excel.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/power-bi-datasets-in-excel.png#lightbox)

The Power BI service can use and apply Sensitivity labels to data models and reports. In the case of a report that uses multiple sensitivity labels, the most sensitive label will take precedence. The Power BI Service will list the type of Sensitivity Label applied - if any - along with whether the dataset is endorsed or not. When Excel connects to a Power BI data source, these labels will still apply!

[![Screenshot of an Excel file with the Highly Confidential sensitivity tag.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-sensitivity-label.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-sensitivity-label.png#lightbox)

In Excel, when a user is building a PivotTable that is connected to Power BI with row-level security (RLS), they will only see the data that is available to them based on the role that's assigned. The RLS roles flow through to Excel, allowing a data modeler to control what the users can view, even if they connect to the dataset from Excel and build a Pivot Table. The Power BI RLS roles assigned to the active user will define the data available to them.

[![Screenshot of different Row Level Security groups with a Pivot Table filtered based upon user access limited by Row Level Security.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-rls-pivottable.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-rls-pivottable.png#lightbox)


# Convert PivotTables to formulas

Completed100 XP

-   5 minutes

A PivotTable is one option that you can choose when connecting to a dataset in Excel. However, you might occasionally want the flexibility of the grid in Excel. Cube formulas allow you to still use the dataset while also not being limited to the contiguous range of a PivotTable.

## Activate cube formulas

After adding a PivotTable to the sheet, go to the **PivotTable Analyze** tab. Select the **OLAP Tools** dropdown list. Select **Convert to Formulas**.

[![Screenshot of convert to formulas feature.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/convert.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/convert.png#lightbox)

Your PivotTable formatting has been removed and replaced with cells that contain formulas that retrieve the same data. Cube formulas have the following syntax:

-   Row/Column Headers
    
    CUBEMEMBER(“Dataset Name”,”TableName.FieldName.&Field Value”)
    
-   Values
    
    CUBEVALUE(“Dataset Name”, Row Header Cell Reference, Column Header Cell Reference, Slicer_FieldName)
    

Cube formulas add formatting flexibility, where you can:

-   Add blank rows or columns to space out the data.
    
-   Reference cells with cube formulas in other formulas without errors after a refresh (such as custom subtotals).
    
-   Complete unlimited cell formatting by individual cell or cells that are not dependent on PivotTable style.
# Office 365/Excel 2016+ formulas

Completed100 XP

-   15 minutes

This unit introduces three new formulas that you'll find in Office 365/Excel 2016+ called XLOOKUP(), FILTER(), and LET(). Another way to find out about new features and functionality that have been added to the application is to join Microsoft Office Insiders Program (see the link in the references section at the end of this module).

## XLOOKUP()

XLOOKUP() is a new, more powerful version of VLOOKUP(). It's simpler, faster, and more flexible.

The reasons why XLOOKUP() is more optimal than VLOOKUP() are as follows:

-   Search columns and rows combine VLOOKUP() and HLOOKUP() for a more comprehensive search.
    
-   Search columns to the left replace INDEX() MATCH() patterns, enabling you to use a combination that best works for your search.
    
-   The formula is more robust in that it doesn't "break" when columns are added/deleted.
    

XLOOKUP() includes a syntax with three required parameters. The function performs an exact match by default.

> [![Screenshot of Excel Formula bar with XLOOKUP() function syntax.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/xlookup.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/xlookup.png#lightbox)

XLOOKUP() has the following features:

-   Returns a value from a given column based on a value in another column
    
-   Returns a different value if no result is found
    
-   Searches from the top or from the bottom
    

XLOOKUP() has six parameters with the last three being optional parameters:

-   '**lookup_value**' - Parameter used to define the value you want to find.
    
-   '**lookup_array**' - Array parameter used to specify the column where to find the value.
    
-   '**return_array**' - Array parameter used to define the column to return the value from.
    
-   '**if_not_found**' - If no match is found, return this optional value.
    
-   '**match_mode**' - Optional parameter for specifying exact match, first above/below, or wildcard search.
    
-   '**search_mode**' - Specify search from top or from bottom with this optional parameter.
    

> [![Screenshot of XLookup() examples.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/examples.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/examples.png#lightbox)

In the previous dataset example, notice the XLOOKUP() formula to the right in the black box that shows the returned results. The three examples answer the following questions:

-   **Find Product by ID** - Formula demonstrating finding the Product for Product ID = 109 where the product results are found in a column to the right of the Product ID column.
    
-   **Find City by ZIP** - Example formula demonstrates finding City for ZIP = 21658, which are results located in a column to the left of the ZIP column.
    
-   **Find last Product by City** - This formula demonstrates the use of optional parameters "No Results found" is returned if there's no results found, exact match, and -1 indicates to search from the bottom to the top of the table of data.
    

## FILTER()

FILTER() is a new array function. Adding the formula to a single cell will return a subset of the table, and the other values will spill to the other cells within the result. FILTER() returns rows of data and allows multiple conditions by using **and/or** logic.

FILTER() has the following features:

-   Returns multiple match results for one or more lookup values
    
-   Filters data without needing to [refresh]{.underline}
    
-   Can be nested inside other Excel functions
    

The following details explain the three parameters that are included with FILTER():

-   '**array**' - Parameter used to specify a range of columns and rows to filter.
    
-   '**include**' - Parameter used to provide filtering rule criteria.
    
-   '**if_empty**' - Optional parameter value to return if no rows meet the conditions.
    

> [![Screenshot of a Filter() Single example.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/filter.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/filter.png#lightbox)

The previous dataset example shows the FILTER() formula in the black box with the returned results. Notice that it uses a table instead of a range. We recommend that you always use a table when you can. The previous example filters the SalesTable table, where **Region = West**, and it returns all matching rows within the result.

> [![Screenshot of a Filter() Multiple example.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/filter-multiple.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/filter-multiple.png#lightbox)

This example uses the same dataset but applies three filters to the table. The formula will filter the table on the following criteria (all criteria must be met for the row to be included):

-   Product = Palma UM-01
    
-   Region = West
    
-   Revenue = Greater than USD 1,215.00
    

The formula uses the multiply function because a logical comparison will result in zero (0) for false or one (1) for true. If all conditions are **TRUE**, then 1 * 1 * 1 = 1. However, if any condition is zero (0) or false, then the entire logic is false.

An asterisk (*) is used for **AND** conditions, and the plus (**+**) sign is used for **OR** conditions.

## LET()

The LET() function offers considerable flexibility for complex calculations and provides a simpler way to digest the different pieces of the formula. It combines the ability for storage of calculations and values that use variables with the native formula syntax of Excel.

> [![Diagram of LET() Function Syntax.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/let-function.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/let-function.png#lightbox)

The variables are used to assign a name to a value or calculation. These variables are used to recall the syntax without having to repeatedly rewrite the formula. You can define up to 126 different variables in the function, but at a minimum, you are required to have the three components (variable, value of variable, calculation). You can also take advantage of other array functions like FILTER() within the LET() function. The following example builds on the FILTER() example from earlier but now with variables assigned.

> [![Screenshot of LET() example.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/let-example.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/let-example.png#lightbox)

In the preceding screenshot, numbers one through four are variables and definitions. The last statement is the calculation that uses the variables.

-   ProductRange = Product column range
    
-   Product = Product to filter on
    
-   RegionRange = Region column range
    
-   Region = Region to filter on
    
-   Filter = Filtering on the table for the Product and Region

# Featured tables and lineage

Completed100 XP

-   10 minutes

Power BI offers you the ability to highlight which tables from the dataset should be featured connection options within Excel. In the **Model View** of Power BI, you can select one of your tables and then review the **Properties** pane. Tables include a toggle setting that you can enable to make it a featured table. You will need to update the key column section to be a column with unique values and add more details for the user to learn about the contents of the table.

[![Screenshot of a Power B I table with the featured table slider set to Yes.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/featured-table.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/featured-table.png#lightbox)

[![Screenshot of featured table details.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/featured-table-settings.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/featured-table-settings.png#lightbox)

After updating all featured tables that you want included, save and publish the report to Power BI service.

## Featured tables - end user

The Power BI report author can highlight specific tables from the dataset, and the end user can pull data from these tables directly. You can locate these tables by going to the **Data** tab and selecting the **Data Types** section.

[![Screenshot of the data types drop down menu.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/data-types-menu.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/data-types-menu.png#lightbox)

## Lineage

Anyone who has access to the workspace is able to view the lineage of the dataset. If you select the ellipsis (**...**) at the end of the toolbar of a Power BI report, you can change to the lineage view.

[![Screenshot of lineage view menu.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/lineage-view-menu.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/lineage-view-menu.png#lightbox)

[![Screenshot example of diagram for lineage view.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/lineage-view.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/lineage-view.png#lightbox)

This visual is an excellent way to show how dataflows, datasets, reports, and dashboards are flowing together within a workspace. Additionally, each report has more available options, such as **Analyze in Excel** or **View Usage Metrics**.

## Featured tables and data types

Featured tables constructed in Power BI can also be used to convert individual data items in Excel into data types. These data types provide yet another avenue by which Power BI datasets can enhance and improve data functionality within Excel.

# Excel and Power BI are better together

Completed100 XP

-   5 minutes

Excel is a great application by itself. However, when you use Excel together with Power BI, it becomes even better. Not every report or analysis needs to be in Power BI, and you don't have to choose one and exclude the other. Excel will inherit all of Power BI's sensitivity, certified, and promoted labels, so you can work with confidence that your data is accessible only to authorized users.

[![Diagram for Power B I integration with Excel.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/power-bi-integration-with-excel.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/power-bi-integration-with-excel.png#lightbox)

## Excel key strengths

Excel is a powerful, familiar application that is used by millions worldwide for data collection, sorting, analysis, budgeting, management, and most commonly, for reporting.

[![Diagram listing Microsoft Excel's strengths.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-strengths.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-strengths.png#lightbox)

Great reasons to use Excel are:

-   When you're learning
    
-   When you're performing one-off analysis
    
-   In intensive accounts/finance roles
    
-   When you need specific Excel features and a grid canvas
    
-   Cube formulas, PivotTables, Sparklines, and Pivot Charts
    

## Power BI key strengths

Power BI is more modern. It offers custom visuals, is interactive, provides data story experiences, and Power BI service provides centralized sharing and collaboration.

[![Diagram listing Microsoft Power BI strengths.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/power-bi-strengths.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/power-bi-strengths.png#lightbox)

Compelling reasons to use Power BI include the ability to:

-   Create data models.
    
-   Share with a consumer audience.
    
-   Provide or have polished and interactive experiences.
    
-   Have it available when you need Power BI features.
    
-   Use visuals, bookmarks, RLS, mobile, and more.
    

## Excel together with Power BI complete cycle

Excel is a good option for a simple data collection tool. Connecting Power BI to a form-like data collection tool in Excel is a simple, flexible, and familiar way of getting manual data entry functionality into Power BI. For example, you can fill out an Excel spreadsheet form, drop it into a shared folder, and then watch Power BI pull in those new entries. The experience will be as if you have written directly into Power BI.

[![Diagram of Excel as a data input for Power BI and Power BI as the output through Analyze in Excel.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/input-output.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/input-output.png#lightbox)

Visuals, reports, and datasets in Power BI can be analyzed in and exported to Excel. Likewise, Power BI can import Excel data models and files for analysis. Each has different strengths that you can use interchangeably, one can feed the other and vice versa.

In this demo, you’ll see how you can use Power BI together with Excel to create a highly customizable report in Excel using a data model published to the Power BI Service.


# Exercise - Creating an Excel report using a Power BI Dataset

Completed100 XP

-   30 minutes

## Overview

The estimated time to complete this exercise is 30 minutes.

In this exercise, you will complete the following tasks:

1.  Publish a Power BI Desktop Dataset & Report to the Power BI service
2.  Download, Install, and Use Analyze in Excel
3.  Build an Excel Report using a Power BI Dataset

 Note

This exercise has been created based on the sales activities of the _fictitious_ Wi-Fi company called SureWi which has been provided by [P3 Adaptive](https://p3adaptive.com/). The data is property of P3 Adaptive and has been shared with the purpose of demonstrating Excel and Power BI functionality with industry sample data. Any use of this data must include this attribution to P3 Adaptive. If you have not already, download and extract the lab files from [https://aka.ms/modern-analytics-labs](https://aka.ms/modern-analytics-labs) into your **C:\ANALYST-LABS** folder.

## Exercise 1: Publish a Power BI Desktop Dataset & Report to the Power BI service

In this exercise, you will use Power BI Desktop to publish your Dataset and Report to My workspace in the Power BI service.

### Task 1: Launch Power BI Desktop

In this task, you will launch Power BI Desktop and open a PBIX file.

1.  Launch Power BI Desktop.
2.  If applicable, use the "x" in the upper right-hand corner to close the Welcome window.

### Task 2: Open the PBIX file

In this task, you will navigate and open the starting PBIX file with the Dataset and Report created from Lab 02.

1.  Select **File** > **Open report** > **Browse reports**.
    
    [![Screenshot of open report window with the Browse reports button.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/browse-reports.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/browse-reports.png#lightbox)
    
2.  Navigate to the **C:\ANALYST-LABS\Lab 03A** folder.
    
3.  Select the file **MAIAD Lab 03A - Power BI Model.pbix** and choose **Open**.
    

### Task 3: Publish the PBIX file to the Service

In this task, you will publish the Dataset and Report from the Power BI Desktop file to the Power BI service.

1.  First, you will need to sign in to Power BI. Click on **Sign in** located in the upper right-hand corner of Power BI Desktop.
    
    [![Screenshot of sign in located in the upper right-hand corner of Power B I Desktop.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sign-in.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sign-in.png#lightbox)
    
2.  Next, you will need to enter your Power BI **username** and **password**. Once signed in, you will notice the Sign-in changes to become your name.
    
    [![Screenshot of sign in window.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sign-in-window.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sign-in-window.png#lightbox)
    
3.  From the **Home** tab in the main menu, select the **Publish** button.
    
    [![Screenshot of Power B I main menu Home tab and Publish button.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/home-tab.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/home-tab.png#lightbox)
    
4.  Select My workspace.
    
    [![Screenshot of publish to Power B I window with My workspace.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/workspace.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/workspace.png#lightbox)
    
5.  Choose the Select button to publish the data model and report page to the Power BI service.
    
     Note
    
    All users have My workspace in Power BI service. This is your _personal_ sandbox. Every organization has different Workspaces. Workspaces can be created, and users can be added to Workspaces to share Datasets and Reports across the organization.
    
6.  Once the publish is successful, you will see the **Success!** message with a link that you can click to open the report in the Power BI service.
    
7.  Click on the Open **MAIAD Lab 03A - Power BI Model.pbix** in Power BI link.
    
    [![Screenshot of publishing to Power B I window with success message.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/success.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/success.png#lightbox)
    
    After clicking on the link, you will be navigated to your browser where you will see your report published to Power BI service in your My workspace location.
    
     Note
    
    To navigate directly to Power BI service enter the URL: [https://app.powerbi.com](https://app.powerbi.com/groups/me/reports/0a9c5249-218c-41d0-b48f-9d66c93f5e52/ReportSection) in your browser.
    
    [![Screenshot of Power B I Service with M A I A D - Power B I Report displayed.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/report-displayed.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/report-displayed.png#lightbox)
    
     Note
    
    Selected report page, slicers and filters are captured as default settings when published to the Power BI service.
    

## Exercise 2: Download, install, and use Analyze in Excel

In this exercise, you will download the Analyze in Excel libraries and use Analyze in Excel to connect to the published **MAIAD Lab 03A - Power BI Model** in Power BI from within the Excel application.

### Task 1: Download Analyze in Excel updates

In this task, you will download a one-time download of Excel libraries that enables Excel to connect to Power BI Datasets.

1.  From within the Power BI service, select **Analyze in Excel updates** from the Downloads menu, which is in the upper right corner.
    
2.  Select the **Download** button.
    
    [![Animated screenshot of a demonstration how to download Analyze in Excel updates from the Power B I Service.](https://learn.microsoft.com/en-us/media/download-install-analyze-in-excel.gif)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/download-install-analyze-in-excel.gif)
    

### Task 2: Install Analyze in Excel

In this task, you will install the Excel libraries that enable Excel to connect to Power BI Datasets.

1.  Once the download completes, the installation file will be in your default Downloads folder. Navigate to your downloaded file and **Double-Click** the file to launch the (.msi) installer wizard.
    
    [![Screenshot of My Downloads folder and the downloaded M S I file.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/open.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/open.png#lightbox)
    
     Note
    
    You can open this file directly from your browser's Downloads section. For Firefox this is in the top right corner. For Internet Explorer this is the bottom left. Download location varies by browser.
    
2.  Follow the wizard steps to install the Analyze in Excel libraries.
    
    [![Screenshot of Analyze in Excel install wizard window.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/next.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/next.png#lightbox)
    

### Task 3: Launch Analyze in Excel from Datasets + dataflows

In this task, you will navigate to the Datasets + dataflows location in the Power BI service to launch Analyze in Excel using the "MAIAD Lab 03A - Power BI Model" Dataset.

1.  From the left-hand pane navigation, select **My workspace**.
    
2.  Select the **Datasets + dataflows** navigation option.
    
    [![Screenshot of Power B I Service with M A I A D - Lab 03 - Power B I Model displayed in Data sets from My workspace.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/datasets-dataflows.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/datasets-dataflows.png#lightbox)
    
     Note
    
    When you publish your PBIX file to the service, there are two Power BI artifacts created: the Data Model will be in **Datasets + dataflows** and Report Pages will be in **Reports**.
    
3.  From the **MAIAD Lab 03A - Power BI Model** Dataset select **More options** and then choose the **Analyze in Excel** menu option.
    
    [![Screenshot of Power B I Service Dataset More menu showing the Analyze in Excel option.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/analyze-excel.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/analyze-excel.png#lightbox)
    

### Task 4: Launch the Analyze in Excel file

In this task, you will launch the Excel file that has been connected to the **MAIAD Lab 03A - Power BI Model** Data Model.

1.  Navigate to your Downloads folder, find the downloaded Excel file and **Double Click** the file to open.
    
    [![Screenshot of My Downloads folder with the Excel file selected in Windows Explorer.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-open.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/excel-open.png#lightbox)
    
     Note
    
    You can open this file directly from your browser's Downloads section. For Firefox this is in the top right corner. For Internet Explorer this is the bottom left. Download location varies by browser.
    
2.  Once Excel launches, you may need to click the buttons to **Enable Editing** and **Enable Content**. This allows Excel to connect to the data model published to the Power BI service, which is an external data connection to Microsoft's Azure storage in the cloud.
    
    [![Screenshot of Enable Editing and Enable Content message and buttons.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/enable-message.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/enable-message.png#lightbox)
    
     Note
    
    If you are not prompted with both the Enable Editing and Enable Content messages, you may need to check your Options > Trust Center > Trust Center Settings... to ensure your Message Bar Settings are turned on.
    

## Exercise 3: Build an Excel report using a Power BI Dataset

In this exercise, you will create a report in Excel using the Power BI Dataset connected to "MAIAD Lab 03A - Power BI Model" created using Analyze in Excel. The Excel report will contain a Pivot Table, a Pivot Chart, and CUBE formulas.

### Task 1: Add Measures to the Pivot Table Fields Values

In this task, you will populate the Pivot Table with Measure fields from the Power BI Dataset connection.

1.  From the **Pivot Table Fields** window, select the Gear icon and change to the Fields Section and Areas Section Side-By-Side option.
    
    [![Screenshot of Pivot Table Fields highlighting the Gear icon.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/gear.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/gear.png#lightbox)
    
     Note
    
    By default, the Pivot Table Fields are displayed with the **Fields Section and Areas Section Stacked**. The instructions that follow have the Pivot Table Fields displayed as **Fields Section and Areas Section Side-By-Side**.
    
2.  From the **Offices** measure table, drag the [# of Offices] measure to the **Values** section in the Pivot Table Fields List.
    
3.  From the **Contracts** measure table, click the **checkbox** for the [Total Contracts] & [MRR Won - Contracts] measures to the **Values** section in the Pivot Table Fields List.
    
    [![Screenshot of Pivot Table Fields List window with the measures in the Values section.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/measures.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/measures.png#lightbox)
    
     Note
    
    When selecting fields from the measure tables, the checkbox will move the field into the Values section by default. This is because only measures can go into the Values section of a Pivot Table Field List when connecting Excel to a Power BI service Dataset.
    
4.  Right click on the Pivot Table, select the **Pivot Table Options**...
    
    [![Screenshot of Pivot Table menu displaying the Pivot Table Options menu item.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/options.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/options.png#lightbox)
    
5.  Select Display and then de-select the checkbox to **Show the Values row**.
    
    [![Screenshot of Pivot Table Options window with the Show the Values row check box de-selected.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/values-row.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/values-row.png#lightbox)
    
     Note
    
    This is done for aesthetics purposes to remove the row with **Values** in the heading that happens by default when adding more than one measure into the Values section of the Pivot Table Fields.
    

### Task 2: Add Fields to the Pivot Table Fields Rows

In this task, you will populate the Pivot Table with Lookup fields from the Power BI Dataset connection.

1.  From the **Offices** field table, drag the [Region] and [District] columns to the **Rows** section in the Pivot Table Fields List.
    
    [![Screenshot of Pivot Table Fields List window with the fields from the Offices table in the Rows section.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/fields.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/fields.png#lightbox)
    
2.  Use the mouse to place the cursor in **Cell A1** and type the name **Region & District** into the cell to change the default heading name.
    
    [![Screenshot of close up of the Pivot Table header to show the label in column A row 1.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/label.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/label.png#lightbox)
    

### Task 3: Insert a Pivot Chart

In this task, you will insert a Pivot Chart workspace into the Excel worksheet to the right of the Pivot Table. Then you will add fields to the Axis and Values sections.

1.  Use your mouse to select **Cell E1** on the worksheet. This is the selects the location for the Pivot Chart.
    
    [![Screenshot of Worksheet with column E row 1 selected for location of new Pivot Chart.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/location.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/location.png#lightbox)
    
2.  Select the **Insert** tab on the main menu and select the **Pivot Chart** option from the **Pivot Chart** button drop-down.
    
    [![Screenshot of Insert tab on main menu with Pivot Chart button drop down selected and Pivot Chart option.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivotchart.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivotchart.png#lightbox)
    
3.  On the Create Pivot Chart window, select the **Use an external data source** radio button.
    
4.  Select the **Choose Connection**... button.
    
    [![Screenshot of Create Pivot Chart window showing the Use an external data source radio button selected and the Choose Connection button.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/connection.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/connection.png#lightbox)
    
5.  Then from the **Connections** tab and the **Connections in this Workbook** section, select the `pbiazure//api.powerbi.com` connection string path name to connect the Pivot Chart to the Power BI Dataset external data source.
    
    [![Screenshot of Existing Connections window with the Connections tab selected, Connections in this Workbook section with the Power B I Service Azure connection path.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/workbook-connections.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/workbook-connections.png#lightbox)
    
     Note
    
    The exact name of your pbiazure://api.powerbi.com connection string will be different than the one shown in the above image. This is the unique connection location identifier for a published Power BI dataset artifact.
    
6.  Click **OK**.
    
7.  From the **Quotes** measure table, click the **checkbox** next to the [Won vs Potential MRR] measure to move the measure into the **Values** section in the Pivot Table Fields List.
    
8.  From the **Offices** field table, drag the [Region] to the **Axis (Categories)** section in the Pivot Table Fields List.
    
    [![Screenshot of Pivot Table Fields with measure from the Quotes table in the Values.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-fields.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-fields.png#lightbox)
    

### Task 4: Format Pivot Chart

In this task, you will format the Pivot Chart using some of the familiar formatting options in Excel.

1.  From the **Design** tab in the main menu, select **Style 4**.
    
    [![Screenshot of Design tab on the main menu with Style 4 selected.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/design.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/design.png#lightbox)
    
2.  Double-click into the Chart Title and change the default Title text to **MMR Won % by Region**.
    
3.  Use the mouse to hover over the upper right-hand side of the Pivot Chart to display the Chart Elements options and **de-select the Legend checkbox** to remove the Legend.
    
    [![Screenshot of Pivot Chart Chart Elements with the Legend checkbox de-selected.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/legend.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/legend.png#lightbox)
    

### Task 5: Add KPIs using CUBEVALUE

In this task, you will use CUBE formulas to create high-level KPIs for the report.

1.  Rename the **data connection** with a friendly name. Click on Data -> Queries & Connections to open the **Queries & Connections** along the right-hand side.
    
    [![Screenshot of Excel Data Tab Queries and Connections button with visual of Connections selected in pane.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/queries-connections-pane.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/queries-connections-pane.png#lightbox)
    
     Note
    
    The exact name of your `pbiazure://api.powerbi.com` connection string will be different than the one shown in the above image. This is the unique connection location identifier for a published Power BI dataset artifact.
    
2.  Select **Connections**, right-click, choose **Properties**, change the connection name to **Power BI - MAIAD Lab 03A – Power BI Model**, and then press ok.
    
    [![Screenshot of Excel Data Connection Properties with new name in Connection name box alongside image of Properties button.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/rename-data-connection.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/rename-data-connection.png#lightbox)
    
     Note
    
    Best practice when referencing data models within Excel is to provide user friendly names for reference and to provide a detailed description about the data connection.
    
3.  Use a **right-click on row 1** to **Insert** a row above the Pivot Table and Pivot Chart.
    
4.  Use **CTRL+Y** to repeat the last step and add another row above the Pivot Table and Pivot Chart.
    
5.  Use a **right-click on column A** to **Insert** a column before the Pivot Table.
    
     Note
    
    This provides a row and column buffer for aesthetics purposes. And provides a row for a report heading and the KPIs using CUBEVALUE formulas.
    
6.  Right-click **column A and set the column with to 1**.
    
7.  Use **Fill Color = Black** from the **Home** tab on the main menu to create a report heading in row 2.
    
8.  Use **Font Color = Gold, Accent 4** for row 2.
    
9.  Select **Cell I2** and enter the text **"Potential MRR:"** - this will serve as the KPI description.
    
10.  In **Cell J2** enter the following CUBEVALUE formula and hit Enter:
    
    =CUBEVALUE("Power BI - MAIAD Lab 03A – Power BI Model","[Measures].[Potential MRR]")
    
    [![Screenshot of Formula bar with measure access.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/measure-access.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/measure-access.png#lightbox)
    
     Tip
    
    As you type the CUBEVALUE formula, you will notice that Intellisense displays to guide you as to the syntax needed to complete the formula. A CUBEVALUE formula can be combined for use with Slicers.
    
11.  Select **Cell K2** and enter the text **"Won MRR:"** - this will serve as the KPI description.
    
12.  In **Cell L2** enter the following CUBEVALUE formula and hit Enter:
    
    =CUBEVALUE("Power BI - MAIAD Lab 03A – Power BI Model","[Measures].[MRR Won - Contracts]")
    
    [![Screenshot of Formula bar with cubevalue function for calculating using a measure from the data model.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/cube-value.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/cube-value.png#lightbox)
    
    Select **Cell M2** and enter the text **"% Won:"** - this will serve as the KPI description.
    
13.  In **Cell N2** enter the following Excel formula and hit Enter:
    
    =L2/J2
    
    [![Screenshot of Formula bar with an Excel cell division formula.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/formula-bar.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/formula-bar.png#lightbox)
    
     Tip
    
    You can combine the familiarity and features of Excel with Dataset published to Power BI!
    
14.  Using a **right-click**, select **Format Cells**... to **percentage**.
    
15.  Select **File** from the Main Excel Ribbon Menu, then **Save As**.
    
16.  Navigate to the **C:\ANALYST-LABS\Lab 03A** folder.
    
17.  Save the file as **MAIAD Lab 03A - Power BI Model - My Solution.xlsx**.
    

In this exercise, you published a Power BI Desktop Dataset and Report to the Power BI service. Then you created a report in Excel with a Pivot Table, Pivot Chart, and CUBE functions connected to a Power BI Dataset. This final exercise illustrates what is possible when you use Power BI together with Excel.

> [![Screenshot of the final Excel report with Pivot Table, Pivot Chart, and Cube Value formulas.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/final-report.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/final-report.png#lightbox)

 Important

Now that you have your report created, you will want to keep it updated. But do not worry, it takes just two button clicks: **Data** > **Refresh All**.

> [![Screenshot of data tab on main menu with Refresh All button displayed.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/refresh.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/refresh.png#lightbox)

# Exercise - Excel and Power BI service better together

Completed100 XP

-   30 minutes

## Overview

The estimated time to complete this exercise is 30 minutes.

In this exercise, you will complete the following tasks:

1.  Use Excel to create a pivot table from a Dataset published in the Power BI service
    
2.  Add Sparkline Charts
    

 Note

This exercise has been created based on the sales activities of the _fictitious_ Wi-Fi company called SureWi which has been provided by [P3 Adaptive](https://p3adaptive.com/). The data is property of P3 Adaptive and has been shared with the purpose of demonstrating Excel and Power BI functionality with industry sample data. Any use of this data must include this attribution to P3 Adaptive. If you have not already, download and extract the lab files from [https://aka.ms/modern-analytics-labs](https://aka.ms/modern-analytics-labs) into your **C:\ANALYST-LABS** folder.

## Exercise 1: Use Excel to create a Pivot Table from a Data Set in the Power BI service

In this exercise, you will use Excel to connect to a published Data Set in the Power BI service.

### Task 1: Launch Excel

In this task, you will launch a new blank worksheet to get started.

1.  Launch Excel.
    
     Note
    
    If you have not already signed in to your O365 account, you may be prompted to sign in, use your work email address and password to sign into your account.
    
2.  Create a new blank workbook.
    

### Task 2: Use Insert new Pivot Table from Power BI

In this task, you will create a new Pivot Table workspace connected to a published data set in the Power BI service.

1.  Select the **Insert** tab on the Main Excel main ribbon menu.
    
2.  Choose **PivotTable** > **From Power BI**.
    
    > [![Screenshot of Insert tab with PivotTable button and From Power BI displayed.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-button.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-button.png#lightbox)
    
3.  If you have many published Data Sets, you can use the **Search** option to type in "Lab", then select the **MAIAD Lab 03 - Power BI Model** data set from the available data set options.
    
    > [![Screenshot of Power BI Datasets window.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/datasets-window.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/datasets-window.png#lightbox)
    
4.  Notice you have a new Pivot Table workspace and the PivotTable Fields with Measure and Field tables.
    
     Note
    
    Measure tables are identified by the summation icon. This behaviour occurs when Excel connects to a Power BI data set. All Measures that can ONLY go into the Values of the PivotTable Fields will be in located in the summation icon table name. And any of the columns or calculated columns that are used for Filters, Columns, or Rows are located in a table icon of the same name.
    
    > [![Screenshot of New Excel workbook connected to MAIAD Lab 03 in the Power BI service displaying new Pivot Table workspace and PivotTable Fields.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/workbook-connected.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/workbook-connected.png#lightbox)
    
     Note
    
    On the right-hand side of the PivotTable Fields window, notice the icons that allow you to toggle the window between Power BI Datasets or PivotTable Fields.
    
    > [![Screenshot of PivotTable Fields close-up showing the Power BI Datasets and PivotTable Fields icons.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-fields-icon.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-fields-icon.png#lightbox)
    

### Task 3: Add Measures to the PivotTable Fields Values

In this task, you will populate the PivotTable with Measure fields from the Power BI Dataset connection.

1.  From the **Contracts** measure table, drag the [Raw MRR per Office] measure to the **Values** section in the PivotTable Fields List.
    
    > [![Screenshot of PivotTable Fields with measure in the Values.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/measure-values.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/measure-values.png#lightbox)
    

### Task 4: Add Fields to the PivotTable Fields Rows

In this task, you will populate the PivotTable with Lookup fields from the Power BI Dataset connection.

1.  From the **Offices** field table, drag the [Region]and [District] fields to the **Rows** section in the PivotTable Fields List.
    
     Note
    
    Lookup field tables are identified by the table with fields icon.
    
    > [![Screenshot of PivotTable Fields window displaying the fields in the Rows.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/fields-rows.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/fields-rows.png#lightbox)
    
2.  From the **Dates** field table, drag the [Year] field to the **Columns** section in the PivotTable Fields List.
    
    > [![Screenshot of Excel workbook showing the Year in Columns and Pivot Table results.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/year-results.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/year-results.png#lightbox)
    

### Task 5: Add Slicers

In this task, you will Add Slicers connected to the Pivot Table.

1.  If the PivotTable Fields list does not display, click on the Pivot Table to make it _active_ and then use a right click and choose **Show Field List**.
    
2.  In the PivotTable Fields, locate the **Customers** Lookup fields table, right-click on the [Company Size] field.
    
3.  Select the **Add as Slicer** option.
    
     Note
    
    The Slicer will just appear in a random location the worksheet, we will reposition the Slicer in the next task.
    
4.  You can also add a Slicer from the Main ribbon menu. Click on the Pivot Table to make it active and then click on the **PivotTable Analyze** tab in the Main ribbon menu.
    
5.  Click the **Insert Slicer** button.
    
6.  From the **Customers** Lookup fields table, click the checkbox next to the [Segment] field.
    

### Task 6: Move & Format Slicers

In this task, you will insert blank Rows and Columns to make space for the Slicers to create a mindful report design for the end users.

1.  Right-click on Column A and **Insert 1 blank column** to the left of the Pivot Table.
    
2.  Right-click on Column A to resize the Column Width to 1.
    
    > [![Screenshot of Worksheet displaying column width of A to 1.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/column-width.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/column-width.png#lightbox)
    
3.  Right-click in Row 1 and **Insert 1 blank row** above the Pivot Table.
    
4.  Use **CTRL+Y** to repeat the insert **five times** to create a total of 6 blank rows above the Pivot Table. This will provide space for our Slicers above the Pivot Table.
    
5.  Drag the **Company Size slicer** above the Pivot Table.
    
6.  With the Company Size slicer selected, choose the **Slicer** tab on the Main ribbon menu.
    
7.  Change the Slicer Buttons number of Columns to 3.
    
    > [![Screenshot of Slicer tab options and Buttons options.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/slicer.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/slicer.png#lightbox)
    
8.  Change the Slicer Style color to **Dark Blue**.
    
    > [![Screenshot of Slicer tab options and Slicer Styles.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/slicer-options.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/slicer-options.png#lightbox)
    
9.  Drag the **Segment slicer** above the Pivot Table and to the right of the Company Size slicer.
    
10.  With the Segment slicer selected, choose the **Slicer** tab in the Main ribbon menu.
    
11.  Change the Slicer Buttons number of Columns to 5.
    
12.  Change the Color to **Dark Blue**.
    
    > [![Screenshot of Worksheet displaying re-positioning of Slicers.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/reposition.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/reposition.png#lightbox)
    

### Task 7: Add Report Title & Format Pivot Table

In this task, you will add a title for the Report and apply final formatting to the Pivot Table.

1.  In cell B2, enter the Report title **MAIAD - Lab 03B - Excel & Power BI service - better together** and use **CTRL + B** to make the font bold.
    
2.  In cell B8, enter the Pivot Table row title **By Region & District**.
    
3.  In cell C7, enter the Pivot Table column title **By Year**.
    
    > [![Screenshot of Worksheet with Report Title and Pivot Table Rows and Column Headings.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/title-rows-headings.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/title-rows-headings.png#lightbox)
    
4.  Click in the Pivot Table to make it active.
    
5.  Select **Design** from the Main ribbon menu > **Subtotals** button > **Subtotals at Top of Group** option. This will create Subtotals for each Region in the Pivot Table.
    
6.  Highlight Columns C to J and with a right-click, change the Column Width to 12.
    
7.  With the Columns C to J still highlighted, select the **Center** Alignment from the Home tab on the Main ribbon menu.
    
    > [![Screenshot of Home tab with Center Alignment.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/center.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/center.png#lightbox)
    
8.  Expand the Segment Slicer so that each of the values is fully visible to the end user.
    
9.  Right-click on the Pivot Table and select **PivotTable Options...**
    
10.  From the Layout & Format tab, de-select the **Autofit column widths on update** checkbox.
    
    > [![Screenshot of Autofit column widths on update check-box.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/autofit.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/autofit.png#lightbox)
    

## Exercise 2: Add Sparklines

In this exercise, you will create Sparkline charts to display the Year trend next to the Pivot Table.

### Task 1: Create Sparkline chart

In this task, you will create a Sparkline chart, combining features in Excel with a Data Model published to the Power BI service.

1.  Position your cursor in cell **K9** then choose **Insert** from the main ribbon menu and select the **Line** button.
    
    > [![Screenshot of Insert menu options with Line button in Sparklines.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sparklines.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sparklines.png#lightbox)
    
2.  Enter the Data Range for the **Central Region** and the Years 2013 to 2017 (D9:H9). Then select the **OK** button.
    
3.  From the Sparkline menu options, select the **Sparkline Color drop down** and change to **Green, Accent 6**.
    
    > [![Screenshot of Sparkline menu with Sparkline Color palette displayed.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sparkline-color.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/sparkline-color.png#lightbox)
    
4.  From the Sparkline menu options, select the **Marker Color drop down** and add a **Green, Accent 6** High Point. Then add a **Dark Red** Low Point.
    
    > [![Screenshot of Marker Color Low Point set to Dark Red.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/dark-red.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/dark-red.png#lightbox)
    
5.  In Column K, copy/paste the Sparkline for each of the Region rows.
    
6.  In cell K8, enter the title **Completed Year Trend**.
    
    > [![Screenshot of Column K with Sparkline Charts.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/charts.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/charts.png#lightbox)
    
7.  Hold the **CTRL** key and highlight each of the Region rows (9, 13, 16, 19, and 23) and then with a right-click, select the **Row Height**... and change to 20.
    
    > [![Screenshot of Pivot Table with Region Rows highlighted and Row Height changed to 20.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/row-height.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/row-height.png#lightbox)
    

### Task 2: Final Formatting

In this task, you will create a final polished report by removing the Excel Headings and Gridlines.

1.  From the main ribbon menu, select the **View** tab.
    
2.  De-select the **Formula Bar**, **Headings**, and **Gridlines** check boxes.
    
    > [![Screenshot of View menu with Formula Bar, Gridlines and Headings options de-selected.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/view-menu.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/view-menu.png#lightbox)
    
3.  Select the Pivot Table and use a **right-click** to display the **PivotTable Options** and de-select the **Autofit column widths on update check box**. This will keep the Pivot Table column widths when slicers are selected.
    
    > [![Screenshot of PivotTable Options window.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-options-window.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/pivot-table-options-window.png#lightbox)
    

### Task 3: Save the Excel file

In this task, you will save the Excel file.

1.  From the main ribbon menu, select **File** > **Save**.
    
2.  Navigate to the **C:\ANALYST-LABS\Lab 03B** folder.
    
3.  Save the file as **MAIAD Lab 03B - Solution.xlsx**.
    

In this exercise, you started in the Excel application and connected to a published data set in the Power BI service to create a Pivot Table with Slicers and Sparkline charts, demonstrating how Excel + Power BI is used better together!

> [![Screenshot of Completed Lab 04 solution.](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/completed-lab.png)](https://learn.microsoft.com/en-us/training/modules/modern-analytics-excel/media/completed-lab.png#lightbox)