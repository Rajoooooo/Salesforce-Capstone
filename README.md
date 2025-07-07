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

## Milestone 4: Field & Relationship

This document summarizes the successful setup and configuration of multiple custom objects within Salesforce to support a travel booking system. The key objects configured include: Customer Info, Booking, Booking Guest, Travel Package, Payment, Employee, and Feedback.

For each object, I created all the necessary fields as per the project requirements, carefully selecting the appropriate data types such as Text, Number, Picklist, Email, Date, Lookup, and Formula. Notably, for the Customer Info object, I created fields such as Email, Country, City, and a formula field to calculate Age using the customer's birthdate. I used Global Picklist Value Sets for Country and City to maintain consistent dropdown values across related objects.

In addition, I created Custom Tabs for all major objects including Booking, Booking Guest, Travel Package, Payment, Employee, and Feedback, ensuring they are easily accessible in the Salesforce app navigation.

Overall, this setup establishes a structured and scalable data model that supports a fully functional travel booking system within Salesforce, with consistent picklist usage, calculated fields, and clear user accessibility through tabs.

## Milestone 5: Field Dependencies

In this project, I used Field Dependencies in Salesforce to make my forms more dynamic, user-friendly, and context-sensitive. Field dependencies allowed me to control which picklist values appear based on what the user selects in another field, helping reduce data entry errors and improving the overall experience.

A field dependency consists of two parts: the Controlling Field and the Dependent Field. The controlling field is the picklist (or checkbox) that determines which values should be shown in the dependent field. For example, when a user selects a country in the controlling field, only the cities related to that country appear in the city picklist. This makes the form cleaner and more relevant for users.

I implemented this feature specifically in the Booking Guest object, where I made Country the controlling field and City the dependent field. This helped ensure that users only see valid city options based on their country selection. Using field dependencies not only streamlined the data input process but also enforced important data relationships without requiring any custom automation.


