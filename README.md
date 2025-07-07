## Milestone 1: Salesforce Account
Salesforce Developer Org Setup
This project documents the steps I followed to create my Salesforce Developer Org for learning and development purposes.

# What I Did
Went to https://developer.salesforce.com/signup

Filled in the form with:

Job Title: Developer

Company: Developer

Clicked "Sign Me Up"

Verified my email and set my password

Logged in at https://login.salesforce.com

## Milestone 2: Object Creation
This document outlines the process of creating a custom object in Salesforce named Customer Info, which is designed to store and manage customer-related data. The object includes support for reporting, search, and field history tracking to enhance visibility and usability across the platform.

To begin, navigate to the Setup area in Salesforce by clicking the gear icon in the upper-right corner. From there, select Object Manager. Once inside the Object Manager, click on Create and choose Custom Object to initiate the creation process.

In the custom object setup form, enter the Label Name as Customer Info and the Plural Label as Customers Info. For the Record Name, specify Customer Name and set the Data Type to Text.

Make sure to enable the following options: Allow Reports, Allow Search, and Track Field History. These settings will ensure that the object can be included in reports, easily searched, and audited for field-level changes over time.

Once all required information is filled out and the appropriate settings are selected, click Save and New to complete the creation of the object and proceed with defining additional fields or related objects.

This setup creates a robust foundation for managing customer information within a custom Salesforce data model.

## Milestone 3: Tabs

To make custom objects easily accessible in the Salesforce interface, I created tabs for each one. I began by going to the Setup page and typing "Tabs" in the Quick Find bar. I then clicked on the Tabs section under the User Interface. Under the Custom Object Tabs section, I clicked New to start the process of creating a new tab.

For the first object, Customer Info, I selected it from the object dropdown and chose a tab style (icon and color) to represent it. I clicked Next, and on the Add to Profiles page, I kept the default visibility settings. On the Add to Custom Apps page, I unchecked the option to include the tab in any app by default but ensured that the option to append the tab to the user's existing personal customizations was checked. I then clicked Save to complete the creation of the tab.

I followed the same exact steps for the remaining custom objects: Booking, Booking Guest, Travel Package, Payment, Employee, and Feedback. Creating these tabs allows each object to be accessed directly from the Salesforce navigation menu, improving usability and enabling quick access for managing records.


