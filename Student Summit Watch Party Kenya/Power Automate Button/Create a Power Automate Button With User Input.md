
Building an instant cloud flow that is triggered by a virtual button is the same as building other Power Automate flows where you've a start and an end. A flow always starts with a trigger action, and this module focuses on manually triggering a flow by using buttons with user input. After you've added the trigger, you'll add steps. Each step can be an action, a condition, or a combination of actions and conditions. The flow always ends with an action.

Two ways to design the process for a button flow are by using an existing template with a button trigger and by building a template from blank.

# Six types of user inputs



Currently, Power Automate flows can have six different types of user inputs:

-   Text
    
-   Yes/No
    
-   File
    
-   Email
    
-   Number
    
-   Date
    

![Screenshot of Manually trigger a flow showing Choose type of user input, and the six user input buttons just listed.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/user-input-button.jpg)

Input type

Description

**Text**

**Text** input is best used for adding text. When you select the ellipsis (...) at the upper-right edge of the screen, you'll see the **Delete** option and three other options: add a drop-down list of options, add a multi-select list of options, and make the field optional.

**Yes/No**

The **Yes/No** input type is best used to select yes or no options.

**File**

The **File** content input type can be used to upload files and images.

**Email**

The **Email** input type is where you would enter an email address. The other inputs complement the use of email input.

**Number**

The **Number** input type is best used to add a numerical value.

**Date**

For the trigger **Date** input type, you can either enter or select a date.

The **Yes/No**, **File**, **Email**, **Number**, and **Date** input types have the same options, for example, to **Make the field optional** and **Delete**.


# Create a Power Automate button that uses all input types


In this unit, you'll create a flow button that will allow a user to report damage that was noticed on the company's property. The data will be saved on a SharePoint list.

1.  Go to the SharePoint online site where you would like to store damage report information.
    
2.  On the upper left of the SharePoint site, select the **+ New** drop-down menu and then select **List**.
    
    [![Screenshot of SharePoint Home page with the New menu expanded and List highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/sharepoint-new-list.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/sharepoint-new-list.jpg#lightbox)
    
3.  Select **+ Blank list**.
    
    [![Screenshot of Create a list with Blank list highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/blank-list.png)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/blank-list.png#lightbox)
    
4.  Give the list a name, such as **Reported Property Damage**. Select **Create**. you'll be automatically redirected to the new list. The list will automatically have the **Title** field option available.
    
    [![Screenshot of the name set to Reported Property Damage.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/list-name.png)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/list-name.png#lightbox)
    
5.  Select **Settings**, which is available on the upper-right edge of the screen and looks like a gear icon. Hovering your mouse over the icon will show the **Settings** option. Next, select **List settings**, which will take you to the **Reported property damage settings** page. In the middle of the screen, you'll see the **Columns** section, which already has the **Title** option available.
    
    [![Screenshot of SharePoint Columns section with the Title column and its type (Single line of text) highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/sharepoint-columns-title.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/sharepoint-columns-title.jpg#lightbox)
    
6.  Select **Title** and change the column name from **Title** to **Location**. Scroll down and select **OK**, which is available on the lower right of the screen.
    
7.  Below the columns, select **Create column**.
    
8.  Enter **Was anyone hurt?** as the column name. Confirm **Single line of text** as the type of column. Scroll down and select **OK** on the lower right of the screen.
    
9.  Follow the previous two steps to add the **Email**, **How many damaged items** and **Anyone you'd like to be CC'ed?** columns.
    
10.  Select **Create column**. Add **Date submitted** as the column name and, this time, select **Date and Time** as the type of column. Scroll down and select **OK** on the lower right of the screen.
    
    [![Screenshot of the Name and Type section with "Date submitted" as the Column name and "Date and Time" as the type of information.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/date-submitted-column.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/date-submitted-column.jpg#lightbox)
    
    The following screenshot shows an example of all the columns.
    
    [![Screenshot of all columns: Location, Was anyone hurt?, Email, How many damaged items, Date submitted, Modified, Created, Created By, and Modified By.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/all-sharepoint-columns.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/all-sharepoint-columns.jpg#lightbox)
    
11.  [Go to Power Automate](https://flow.microsoft.com/) and sign in.
    
12.  On the left vertical menu, select **+ Create**.
    
13.  At the top of the page is the **Three ways to make a flow** heading. Select the **Instant cloud flow** option from the **Start from blank** menu.
    
14.  Enter **Report Property Damage** as your **Flow name** and select the **Manually trigger a flow** option.
    
15.  Select **Create** to start building the button flow.
    
16.  You're now in the Power Automate flow studio with the flow title and the **Manually trigger a flow** trigger already added.
    
    [![Screenshot of Report Property Damage flow with Manually trigger a flow added.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/report-damage-trigger.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/report-damage-trigger.jpg#lightbox)
    
17.  Select the **Manually trigger a flow** trigger and then select **+ Add an input**.
    
18.  Select **Text**. Replace the **Input text** with **Location**.
    
19.  Select **+ Add an input** and select **Yes/No**. Replace **Yes/No** with **Was anyone hurt?**
    
20.  Select **+ Add an input** and select **File**. Replace **File Content** with **Take a picture of the damage**.
    
21.  Select **+ Add an input** and select **Email**. Replace **Email** with **Anyone you'd like to be Cc'd?**
    
22.  Select **+ Add an input** and select **Number**. Replace **Number** with **How many damaged items?**
    
23.  Select **+ Add an input** and select **Date**. Replace **Trigger date** with **Add today's date**.
    
24.  Select **+ New step** and search for **SharePoint**. Under **Actions**, select **Create item**.
    
25.  In the **Create item** action, for **Site Address**, select the drop-down arrow, which is available to the right and then select the site where your list is available. If the site doesn't appear, then select **Enter custom value** and paste the site URL.
    
26.  In the **List Name** field, select the **Reported Property Damage** list that you previously created. After you've selected the list, the column names will appear below it.
    
27.  In the **Location** field on the right, and then in the **Dynamic Content** section, select **Location**.
    
    [![Create item dialog with Location option clicked, showing dynamic content with Location highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/add-location-dynamic-content.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/add-location-dynamic-content.jpg#lightbox)
    
28.  Add Dynamic content for the other fields. After you've completed the steps, the result should look like the following image.
    
    [![Screenshot showing Create item with dynamic fields for Location, Was anyone hurt, Email, How many damaged items, and Date submitted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/all-fields-create-item-action.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/all-fields-create-item-action.jpg#lightbox)
    
29.  Select **+ New step** and search for SharePoint. Under **Actions**, select **Add attachment**.
    
30.  For **Site Address**, select the drop-down arrow, which is to the right, and then select the site where your list is available. If the site doesn't appear, select **Enter custom value** and paste the site URL.
    
31.  In the **List Name** field, select the **Reported Property Damage** list that you previously  
    created. After the list is selected, the column names will appear below it.
    
32.  In the **Id** field, select **ID** dynamic content.
    
33.  In the **File name** field, enter `DamageReportImage.jpeg`.
    
34.  In the **File Content** field, in the **Dynamic Content** section, select **Take a picture of the damage**.
    
    [![Add attachment dialog with the File Content option clicked, showing dynamic content with Take a picture of the damage highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/take-picture-damage.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/take-picture-damage.jpg#lightbox)
    
35.  Select **Flow checker**, which is available on the upper right of the screen. If you've zero errors and warnings, select the **X** and then select **Save**.
    
36.  You can now test the button by using your smartphone. Open the Power Automate app and select the **Buttons** option on the lower horizontal menu. You'll now see the **Report Property Damage** button. Select this button.
    
37.  Populate all the items in the user input fields and then select **Done**.
    
    [![Mobile screenshot showing the sample report.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/sample-report-using-mobile-app.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/sample-report-using-mobile-app.jpg#lightbox)
    
38.  You can return to your list and confirm the new item, including the image that has been added.
    
    [![Screenshot of SharePoint Reported Property Damage list with the image showing as an attachment.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/report-image.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/report-image.jpg#lightbox)
    

Now you've successfully created the app using all six user inputs.

# Create a Power Automate button that sends an email



In this unit, you'll build a button containing a flow. The flow sends an email to your manager with your current location and a photo of the vehicle that you're using.

1.  Sign in to [Go to Power Automate](https://flow.microsoft.com/).
    
2.  Select **+ Create** on the left menu and then select **Instant cloud flow**.
    
3.  Enter **Notify Your Manager** as your **Flow name**. Select the **Manually trigger a flow** trigger, and then select **Create** to start building the flow.
    
    [![Screenshot of Notify Your Manager trigger with Manually trigger a flow added.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/create-name-manager-flow.png)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/create-name-manager-flow.png#lightbox)
    
4.  Select the **Manually trigger a flow** trigger and then select **+ Add an input**.
    
5.  Select **File** and rename **File Content** to **Image**.
    
    [![Screenshot of Manually trigger a flow with an image file added.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/notify-manager-trigger.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/notify-manager-trigger.jpg#lightbox)
    
6.  Select **+ New step** and search for **Office 365 Users**. Under **Actions**, select the **Get manager (V2)** option.
    
7.  In the **User (UPN)** field, select **User email** from the **Dynamic content** window.
    
    [![Screenshot of Manually trigger a flow with Get manager showing the User (U P N) option with the Dynamic content open and User email highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/get-manager-v2.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/get-manager-v2.jpg#lightbox)
    
8.  Select **+ New step** and search for Outlook and select **Office 365 Outlook**.
    
    [![Screenshot of Choose an operation with Office 365 Outlook highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/office-365-outlook.png)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/office-365-outlook.png#lightbox)
    
9.  Under **Actions**, select the **Send an email (V2)** option.
    
10.  In the **To** field, in the **Dynamic content** section, under **Get manager (V2)**, select **Mail**. You might have to select **See more** to find **Mail**.
    
    [![Screenshot of Send an email with Dynamic content for the To field showing and the See more button highlighted next to Get manager.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/mail.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/mail.jpg#lightbox)
    
11.  Set the **Subject** field to `My current location and vehicle I am using`.
    
12.  Set the **Body** field to the following text:
    
    RCopy
    
    ```
    Hi
    
    I have arrived at my current location and attached is a picture of the vehicle I am currently using.
    
    Address:
    ```
    
13.  In the **Body** field, after the word **Hi**, select **Display Name** from the **Dynamic content** window under **Get manager (V2)**.
    
14.  In the **Body** field, below **Address:**, select **Full address**, from the **Dynamic content** window under **Manually trigger a flow**. You might have to scroll down a bit to find it.
    
15.  Select **Show advanced options** to add the photo as an attachment.
    
16.  Set the **Attachments Name - 1** field to any name you would like to use followed by the **.jpg** extension. Then set the **Attachments Content - 1** field to the following expression:
    
    `base64ToBinary(triggerBody()?['file']?['contentBytes'])`
    
    The following screenshot shows what the **Send an email (V2)** action looks like.
    
    [![Screenshot of Send an email with the body filled in with "Hi Display Name (dynamic field) I have arrived... Address: Full address (dynamic field)".](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/send-email-body.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/send-email-body.jpg#lightbox)
    
17.  **Save** the flow.
    
18.  You can now test the button by using your smartphone. Open the app and select the **Buttons** option on the lower horizontal menu. Select the **Notify Your Manager** button. To add an image, select the **paper clip icon** and add an image by taking a new picture with your camera or by using an existing image from your photo library.
    
    Your manager will get an email with an image attached.


# Exercise - Use an existing button template to add a new Outlook task



This exercise shows you how to use an existing button template to add a new Outlook task rather than creating a button flow from blank, which you did earlier in this module.

This exercise uses the **Create new Outlook Task** template.

Follow these steps:

1.  [Go to Power Automate](https://flow.microsoft.com/) and sign in.
    
2.  On the left vertical menu, select **Templates**.
    
3.  Below the **Search templates...** search box are several options such as **All flows**, **Featured**, **Shared with me**, and so on. Find and select the **Button** option.
    
    [![Screenshot of Search templates with the Button option selected.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/button-templates.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/button-templates.jpg#lightbox)
    
4.  Find the **Create new Outlook Task** template and select it.
    
    [![Screenshot of the Create new Outlook task tile from the search results.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/create-new-outlook-task-template.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/create-new-outlook-task-template.jpg#lightbox)
    
5.  Select **sign in**.
    
    A temporary authentication pop-up window might appear and require you to add your username and password.
    
6.  Select **Create Flow**.
    
    Your new flow will automatically be created.
    
7.  You can now test the button by using your smart phone. Open the app and select the **Buttons** option on the bottom horizontal menu. Select the **Create new Outlook Task** button.
    
8.  Add a task name and task description and then select **Done**, which is available on the upper-right side of the app.
    
    [![Mobile screenshot of Create new Outlook Task with the Done button highlighted.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/add-new-outlook-task-using-mobile-app.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/add-new-outlook-task-using-mobile-app.jpg#lightbox)
    
9.  To confirm that the flow has run successfully, go to Outlook on your local machine and select the **Task** icon on the lower left of the screen.
    
10.  Verify that you see the new task.
    
    [![Screenshot of Outlook with the Using button task available in the Task list.](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/new-task-made-available.jpg)](https://learn.microsoft.com/en-us/training/modules/button-user-input/media/new-task-made-available.jpg#lightbox)