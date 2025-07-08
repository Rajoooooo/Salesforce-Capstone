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


## Milestone 6: Validation Rules

To maintain accurate and consistent data in Salesforce, I implemented Validation Rules that enforce specific conditions before a record can be saved. These rules are designed to catch incorrect or incomplete inputs by automatically displaying an error message when the data entered doesn't meet the defined criteria. For example, I created a validation rule to prevent saving a new record unless the Status picklist is set to “Pending.” This ensures that users follow the correct status flow when creating records. I used logical functions like ISNEW() and ISPICKVAL() to define these conditions, and thoroughly tested the rule to make sure it works as intended. By doing this, I was able to improve the reliability of our data and reduce manual errors during data entry.
To ensure data quality in my Salesforce application, I implemented Validation Rules that verify whether the data entered into a record meets specific criteria before it can be saved. I configured these rules so that if a user enters invalid or incomplete information, Salesforce displays an error message and prevents the record from being saved. This helps maintain consistency and accuracy across the system. For example, I created a validation rule to restrict certain picklist values unless other conditions are met, ensuring that users follow the correct process flow when submitting records.

# Milestone 13: The Lighting App

To organize and streamline access to the core features of our travel management system, I created a custom Lightning App in Salesforce named “Tours & Travels CRM.”

I began by navigating to Setup, then typed “App Manager” in the Quick Find box and selected App Manager from the results. On the App Manager page, I clicked “New Lightning App” to start the setup process.

In the App Details & Branding step, I entered “Tours & Travels CRM” as the App Name. I also uploaded a custom image that reflects the theme of tours and travel—this serves as the visual icon for the app and helps with branding. Once the image was uploaded, I clicked Next to proceed.

In the App Options step, I kept the default selections (such as “App Settings” and “Navigation Style”) and continued by clicking Next. Similarly, in the Utility Bar section, I left the default options untouched and clicked Next again.

In the Navigation Items step, I customized the app by selecting the most relevant custom and standard objects. I moved the following from Available Items to Selected Items:

Customers Info

TravelPackages

Booking

Booking Payments

BookingGuests

Employees

Feedback

Task

Reports

Dashboards

These items provide the core functionality of the Tours & Travels CRM and ensure that end users can easily access all essential modules within the app.

In the final step, I configured user access. From the Available Profiles list, I selected System Administrator and moved it to Selected Profiles to give full access to system admins. Once everything was reviewed, I clicked Save & Finish to create and activate the app.

With this setup, the Tours & Travels CRM Lightning App is now available to users with the appropriate profile and provides a centralized workspace tailored for travel-related operations.

## Milestone: 24: Roles and Role Hierarchy

To define clear record-level visibility and ensure proper data access across departments, I created three new roles under the CEO role in Salesforce. These roles help establish a structured role hierarchy, making it easier to manage who can see and access specific records.

I started by going to Setup, then typed “Roles” into the Quick Find box and selected “Set Up Roles.” This brought me to the role hierarchy page where I located the CEO role.

From there, I clicked “Add Role” directly under the CEO node. In the form that appeared, I entered the Label as “Finance Officer Role”—the Role Name field was auto-filled based on the label. I then clicked Save to add the role.

Next, I repeated the same steps to add two more roles under the CEO:

First, I added the “Marketing Executive Role”.

Then, I added the “Customer Service Rep Role.”

Each role was created by clicking Add Role under the CEO, entering the appropriate label, and saving the record.

By setting up these roles under the CEO, I established a clear and scalable hierarchy, ensuring that record visibility aligns with each department's responsibilities while maintaining centralized oversight at the executive level.
