# The Assembler: Creating the Mortgage Approval App

In this part of the sample, the assembler (a business developer) creates an App leveraging a template as a starting point.
___
**Ensure you have the MortgagePA process app imported into Workflow as indicated [here](../README.md).**
___
1. Open BAStudio and ensure the view mode in the user preferences is set to basic. 

![alt text](./images/PrefMenu.png "Preferences Menu")

![alt text](./images/PrefBasic.png "Basic Mode")

2. If you haven't performed the Create Actions and Template steps, then import the "MortgageAppTemplate - V1.twx" file.
3. Go to the template panel and create an App from the MortgageAppTemplate. Name the App MortgageApproval.

![alt text](./images/CreateApp.png "Create the App")

4. The editor is opened to the first page. Add the Customer View by clicking in the upper "Add content here" area. In the Data mapping dialog, click "Select data" and choose to create a new variable. Set the variable name to "customer".

![alt text](./images/CustomerPalette.png "Choosing Customer view from the palette")

![alt text](./images/CustomerDataMap.png "Data mapping for customer view")

5. Add a decimal control under the customer form, set the label to "Mortgage Amount" and create a new variable called mortgageAmount for the data mapping.
6. Add a decimal control under Mortgage Amount, set the label to Yearly Income and create a new variable called yearlyIncome for the data mapping.

![alt text](./images/DecimalFields.png "Mortgage Amount and Yearly Income")

7. Create a button in the bottom "Add content here" area.
8. In the Next step dialog that appears, call the IsMortgageAutoApproved action. The inputs are automatically mapped.  For the output, choose a new variable called "isApproved".
9. Click the plus icon to create a branching path.
10. For the top path, select New Page and call it "Auto Approved".  Set condition to isApproved==true.
11. For the bottom path, select New Page and call it Risk Assessment. Complete the dialog.

![alt text](./images/NextButtonNextSteps.png "Next Steps")

12. Change the label of the button to "Next" using the selection toolbar.  You may optionally change its color and set an icon.

![alt text](./images/NextButton.png "Next Button")

13. Go to the Auto Approved page and set the initial content to CreditDeptTempl.
14. Create Display Text with the content "Mortgage is automatically approved."
15. Create a button in the bottom content box. In the Next step dialog, set the action to "OpenMortgageAccount". The mortgage amount should be automatically mapped.  Create a new variable called customerID for the other input parameter. Choose <end application> for the "Go to page" setting.

![alt text](./images/OpenAccountButton.png "Open Account Button")

16. Set the button label to "Open Account and Exit". You may optionally change its color and set an icon.

![alt text](./images/AutoApprovedPage.png "Auto Approved Page")

17. The customer ID variable is not being populated in the App yet, so go back to the Starting Page, create a Plain Text control under the customer form called "Customer ID". In the data mapping dialog, choose existing data as customerID.

![alt text](./images/CustomerIDDataMap.png "Customer ID Data Map")

18. Add a button under Customer ID and have it call the GetCustomerID action, mapping to the customer and customerID variables. After the action is called, we want to stay on the current page.

![alt text](./images/LookupIDNextSteps.png "Customer ID Lookup Next Steps")

19. Change the button label to "Lookup". You may optionally change its color and set an icon.

![alt text](./images/CustomerIDLookup.png "Customer ID Lookup")

20. Go to the Risk Assessment pageand set the initial content to CreditDeptTempl.
21. We want to show the mortgage amount on this page, so the variable tab of the palette is used to select mortgageAmount.

![alt text](./images/PaletteMortAmount.png "Mortgage amount variable on palette")

22. Create an instance of Loan Risk Charts under the mortgage amount.
23. Create a button in the bottom content box. In the Next step dialog, set the action to "OpenMortgageAccount". Both inputs should be automatically mapped. Choose <end application> for the "Go to page" setting.
24. Set the button label to "Open Account and Exit". You may optionally change its color and set an icon.
25. Create another new button to the right of the other. Set it to go to <end application>.
26. Rename the button to Decline. You may optionally change its color and set an icon.

![alt text](./images/RiskPageButtons.png "Risk Page Buttons")

27. Now that the App is fully authored, press the Test button in the top right corner to try it out. Use "Joe" as the first name for the customer ID lookup to work properly.
28. Once you are happy with how the app is running, return to studio.  Using the menu on the card, choose Request publish. Enter V1 for the snapshot name and complete the dialog so the administrator can publish the app into production.

![alt text](./images/RequestPublish.png "Request Publish")
