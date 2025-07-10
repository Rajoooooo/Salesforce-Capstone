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

## Milestone 7: Approval Process

Before implementing the approval process, I first made sure to complete all required milestones—specifically the setup of Profiles, Roles, and Users—since these components are essential for assigning approval responsibilities and managing record visibility. Once those were in place, I proceeded to build the Booking Cancellation Approval Process.

I began by creating the necessary Classic Email Templates. From Setup, I typed “Email Templates” in the Quick Find box and selected Classic Email Templates. I clicked “New Template”, selected “Text” as the format since it doesn’t require rich formatting, and clicked Next. For the first template, I used the name "Booking Cancellation Approval Notification" and saved it under the Unfiled Public Email Templates folder. I set the subject line to "Approval Needed: Booking {!Booking__c.Name}" and added a message body notifying the assigned approver that a booking cancellation was awaiting approval, including dynamic merge fields like the booking name and owner name.

Next, I created a second template for notifying customers when their cancellation request is approved. I named it "Cancellation Approved". In the body, I inserted dynamic fields like the customer name, travel package, booking number, and travel start date. I also included a confirmation message indicating that the refund will be processed soon. Following that, I created a third template named "Cancellation Rejected". This one notifies the customer when a cancellation is declined, and includes details such as their travel package, booking ID, and travel date, along with a polite message explaining that the request did not meet the required conditions.

Once the email templates were ready, I moved on to configuring the Approval Process itself. From Setup, I typed “Approval Processes” into the Quick Find box and selected Approval Processes under Process Automation. I clicked on the Booking object, then selected “Create New Approval Process” using the Standard Setup Wizard.

For Step 1, I gave the process the name "Booking Cancellation Approval" and kept the auto-generated unique name. I set the Entry Criteria so that the process would only trigger when the Booking Status equals "Cancelled", and the Cancel Confirmation field equals "True". This ensures only valid and confirmed cancellation requests go through the approval process.

In Step 2, I configured the Approver Assignment. I chose to automatically assign the request either to a specific user (like a manager) or to the manager of the user who submitted the record, depending on the use case. I made sure that the relevant users had managers defined in their user profiles.

For Step 3, I selected the "Booking Cancellation Approval Notification" email template to be used as the notification email for approvers. In Step 4, I chose the fields that approvers should see in the approval layout, including Booking Number, Customer, Owner, Travel Package, Cancellation Reason, Travel Start Date, and Total Billing Amount. I added these to the selection and arranged them in a logical order.

For Step 5, I defined the Initial Submitters as users assigned the Travel Agent Role and the Booking Owner. These are the users allowed to initiate the approval request. I then moved to Step 6 to configure Initial Submission Actions—here, I created a Field Update that sets the Booking Status field to "Pending" once the request is submitted.

In Step 7, I defined the Final Approval Actions. First, I created a field update to set the Approval Status to "Approved". Then, I created an Email Alert to send the "Cancellation Approved" template to the customer once their cancellation is approved. The recipient was set to the customer email field, and the sender was configured as the current user.

Step 8 covered the Final Rejection Actions. I created two field updates: one to revert the Booking Status to "Confirmed", and another to set the Approval Status to "Rejected". I also created an email alert that uses the "Cancellation Rejected" email template, which is automatically sent to the customer if their request is denied.

Finally, in Step 9, I added an Approval Step named "Travel Agent Manager Approval". I chose to have all matching records enter this step, and assigned the approver to a specific user—such as Michael Jackson, who was previously created under the Travel Agent Manager Role. This ensures the right person is always notified to take action on cancellation requests.

Once all steps were configured and reviewed, I went to the Approval Process Detail Page and clicked the "Activate" button to deploy it. The process is now live and ensures a structured, consistent workflow for handling booking cancellations, while keeping both internal users and customers informed at every stage.

## Milestone 8: Flows

To ensure data integrity between the number of guests and travelers in our Tours and Travels CRM, I created a Record-Triggered Flow that prevents users from saving a BookingGuest record if it would result in exceeding the number of travelers specified in the related Booking record. I started by going to Setup, searched for Flow in the Quick Find box, and clicked New Flow. I chose Record-Triggered Flow and clicked Create. For the object, I selected BookingGuest, and configured it to trigger when a record is created or updated. I then set the flow to run using the Fast Field Updates option for better performance.

Next, I added a Get Records element to fetch the related Booking record. I named it Get Booking Records, selected the Booking object, and chose to automatically store all fields from the record. After that, I added a Decision element to check if the number of booking guests had exceeded the number of travelers. I labeled it To Check Guests > Travellers, and configured the outcome to compare the value of {!$Record.Booking__r.No_of_Booking_Guests_Info_Available__c} against {!$Record.Booking__r.Number_of_Travelers__c}. If the guest count was higher, the flow would follow the "Yes" outcome path.

To display a proper message, I went to the Toolbox and created a Text Template resource named ErrorMessageTemplate. In the body, I wrote: “Sorry, we can't add more guests because the maximum number of Travellers for this booking has already been reached,” and selected Plain Text view. I then added a Custom Error element under the “Yes” path, labeled it Error Message, set the error location to show in a window on the record page, and used the ErrorMessageTemplate resource as the message.

Finally, I saved the flow as a new version with the label "Show Error if Guests > Travellers", and clicked Activate. With this flow in place, the system now automatically prevents users from exceeding the allowed guest count per booking, improving both user experience and data accuracy.

## Milestone 9: Workflow

To automate customer follow-ups and improve post-trip engagement, I created a Workflow Rule in Salesforce that automatically generates a Task for the Travel Agent to contact the customer for feedback whenever a booking is marked as Completed. From Setup, I searched for and selected Workflow Rules, then clicked New Rule and chose to continue with Workflow Rules. I selected Booking as the object and clicked Next.

I named the rule “Follow-up Task After Booking Completion” and set the Evaluation Criteria to “Created, and every time it’s edited” to ensure the rule runs whenever the booking status changes. For the Rule Criteria, I specified that the rule should run if the Booking Status field equals "Completed". After saving the rule, I clicked Add Workflow Action and selected New Task.

In the task setup, I assigned the task to the Booking Owner and set the Subject to “Follow up for feedback”. For the Due Date, I used the Travelling End Date of the booking and added 3 days to it. I set the Priority to Normal, the Status to Not Started, and added a comment: “Please contact the customer for feedback about the recent trip.” After saving the task and clicking Done, I returned to the Workflow Rule detail page and clicked Activate to turn it on.

Now, each time a booking is completed, Salesforce automatically creates a follow-up task for the travel agent to check in with the customer, helping ensure better service and useful feedback collection.

## Milestone 10: Process Builder

To reduce manual updates and improve efficiency in the Tours and Travels CRM, I created a Process Builder automation that automatically sets a booking’s status to “Confirmed” once a related payment is marked as Completed. From Setup, I searched for Process Builder, clicked New, and named the process "Update Booking to Confirmed When Payment Completed". I set it to start when a record changes and selected Booking Payment as the object, triggering the process when a record is created or edited.

Next, I added a criteria named Payment Completed, where the condition checks if the Payment_Status__c field equals “Completed”. If true, the process runs an immediate action to update the related Booking record, setting its Booking Status to “Confirmed.” After configuring the update, I saved the process and clicked Activate. Now, every time a payment is completed, the booking is automatically updated to confirmed without manual input.

## Milestone 11: Triggers

To automate key parts of the Tours and Travel CRM booking process, I created an Apex trigger and handler class that generate related records automatically. When a new Booking__c record is created, a corresponding Payment__c record is inserted with a default status of "Pending." This ensures that the payment process is immediately tied to each booking.

In the same trigger, I added logic to generate Booking_Guest__c records based on the number of travelers specified in the booking. For every traveler, a guest record is created and linked to the same booking, with placeholder names like "Guest 1", "Guest 2", etc.

These features were implemented using the Developer Console in Salesforce through a trigger (BookingTrigger) and a handler class (BookingTriggerHandler). Together, they streamline the booking workflow, reduce manual data entry, and ensure that essential related records are consistently created and linked.

## Milestone 12: Asynchronous Apex

To automate essential customer communications in the Tours and Travels CRM system, several Apex automation techniques were implemented using Future, Queueable, Batchable, and Schedulable Apex classes. First, a Future method was developed in the BookingConfirmationEmailer class to send confirmation emails to customers when a Booking__c record's status is updated to "Confirmed". The corresponding logic was added in the BookingTrigger to detect this change and asynchronously send the email to the customer using their stored email address.

Next, to send tour reminder emails to customers three days before their scheduled travel date, a Queueable class named BookingReminderQueueable was implemented. It processes a list of upcoming bookings and sends emails accordingly. A Schedulable class, BookingReminderScheduler, was also created to query relevant bookings and enqueue the queueable job. This scheduler is then set to run daily at 6 AM via the UI or System.schedule using a cron expression.

## Milestone 13: The Lighting App

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

## Milestone 14: Editing of Page Layouts

As part of optimizing the user interface in Salesforce, I updated the Page Layouts for several custom objects to improve field organization and ensure better data visibility. First, I navigated to Setup > Object Manager and searched for each object individually using the Quick Find box.

Starting with Customer Info, I accessed the object’s layout under the “Page Layouts” section, rearranged the fields as required for better readability, and saved the changes. I followed the same steps for the BookingGuest object, adjusting the layout to ensure relevant guest details are easily accessible.

Next, I modified the TravelPackage layout, organizing the fields to highlight key travel package information. After that, I updated the Employee layout by arranging the fields logically to display staff information clearly.

I also made layout improvements to the Booking object, ensuring that booking details like status, traveler info, and related data are grouped properly. For the Booking Payments object, I reorganized fields to present payment details more efficiently.

Lastly, I updated the Feedbacks object layout to streamline the visibility of customer feedback records.

Each layout change was finalized by clicking Save, ensuring that the revised configurations were applied successfully across all objects. These updates help streamline the CRM workflow and enhance usability for all users accessing these records.
Lastly, for sending payment reminders to customers whose bookings remain in "Pending" status a day after booking, a Batchable Apex class called PaymentReminderBatch was created. It queries all such records and sends out reminder emails. An accompanying Schedulable class, SchedulePaymentReminderBatch, was built to execute the batch class daily. This scheduled job is configured in Setup > Apex Classes > Schedule Apex, set to run daily at 5 AM from Sunday to Saturday.

These automation enhancements improve customer communication efficiency and ensure timely follow-ups without manual intervention.

## Milestone 15: Dynamic Forms

To enable Dynamic Forms for the Booking object in my Salesforce Tours & Travels CRM app, I first logged in to my Salesforce account and clicked on the App Launcher from the Setup menu. From there, I opened the Tours & Travels CRM App and navigated to the Booking tab. I clicked New, filled out the required details to create a new Booking record, and then saved it.

After creating the record, I clicked on the gear icon in the top-right corner and selected Edit Page to open the Lightning App Builder. On the page layout, I clicked on the Details section. On the right-hand panel, I saw the option to "Upgrade Now" under Dynamic Forms, so I clicked it to begin enabling the feature for this object.

In the upgrade wizard, I selected the layout named "Booking PageLayout" and clicked Finish to apply the changes. Once Dynamic Forms were enabled, I started configuring field visibility. I clicked on the Cancellation Date field, then clicked on Filter in the right pane and set the field visibility rule: I selected Booking Status as the field, Equals as the operator, and Cancelled as the value. I clicked Done to save this filter.

I repeated the same process for the Cancel Confirmation and Approval Status fields—each time setting the visibility filter based on Booking Status equals Cancelled and confirming by clicking Done.

After configuring all field visibility settings, I clicked Save, and then selected Activate to publish the changes. I chose Org Default, selected both Desktop and Phone as the form factors, clicked Next, and finally clicked Save to complete the setup.

## Milestone 16: Users

Before creating any users in Salesforce, I made sure to complete all the necessary setup for Profiles and Roles. This included configuring roles such as Travel Agent Manager, Travel Agent, Finance Officer, Marketing Executive, Customer Service Representative, and Tour Guide, each paired with a custom profile that defines the appropriate level of access. Once these foundational elements were in place, I proceeded to create the users.

To begin, I went to Setup, typed "Users" in the Quick Find box, and selected Users. I clicked New User to create the first record. I entered the following details: First Name as Michael, Last Name as Jackson, an Alias (e.g., mjackson), and my personal email address to receive the activation link. I then assigned a unique Username in the format text@text.text (e.g., m.jackson@tourscrm.com), added a Nickname, and set the Role to Travel Agent Manager Role. I selected the Salesforce Platform as the User License, and assigned the Travel Agent Profile. After verifying all fields, I saved the user, which triggered a welcome email for account setup.

Following that, I repeated the same process to create additional users. I created at least two users for each of the remaining roles: Travel Agent, Finance Officer, Marketing Executive, Customer Service Rep, and Tour Guide. For each user, I ensured the correct role, user license, and profile were assigned, reflecting their specific responsibilities within the Tours and Travels CRM system. This approach helped establish a clean and secure user structure, with appropriate visibility and permissions aligned to each department’s function.

## Milestone 17: Reports

To begin working with reports, I first navigated to the App Launcher and searched for the Reports tab. Once there, I created a new report folder labeled "Revenue Folder". The folder's unique name was auto-generated. After saving the folder, I proceeded to share it by clicking the dropdown arrow next to the folder name under the “All Folders” section. I chose to share it with specific roles—namely, the Travel Agent Manager Role and the Finance Officer Role—and granted them View access.

Next, I created several reports to support business analysis needs. Before creating reports, I ensured that there were 10 recent records in every relevant object, and that all required fields were filled in. Specifically for the Booking object, I made sure that all new records had the Booking Status set to "Pending".

For Report 1, I created a Monthly Revenue Report using the Booking report type. I selected columns such as Booking Number, Customer, Booking Date, and Total Billing Amount, and removed any unnecessary fields. In the filters section, I set the criteria to show all bookings for this month with statuses Confirmed or Completed. I created a Bucket field on Total Billing Amount named Revenue Category, with ranges labeled as Low (0–50,000), Medium (50,001–200,000), and High (over 200,000). I grouped rows by Travel Package and Revenue Category, added a Pie Chart, and saved the report into the Revenue Folder.

For Report 2: Pending Payments, I used the Booking Payments with Bookings report type. I filtered the report to show records where Payment_Status__c = Pending, and selected relevant columns to display payment and booking details. This report was also saved under the Revenue Folder.

For Report 3: Top Travel Packages, I selected the Bookings with Travel Packages report type. I grouped the rows by TravelPackage__r.Name and added a summary count of bookings per travel package. The results were sorted by the highest count, giving a clear view of the most popular travel packages. The report was saved with the name Top Travel Packages.

For Report 4: Employee Roles Distribution, I chose the Employees report type. I grouped rows by the Role__c field and added a count summary to see the number of employees per role. This report was saved as Employee Role Breakdown.

Finally, I created five additional custom reports for other use cases, such as analyzing customer bookings by country, tracking bookings by month, monitoring feedback ratings, assessing package popularity over time, and listing high-value clients. Each report was saved in relevant folders for easy organization and access.

This comprehensive report setup provides valuable insights into booking trends, employee distribution, payment status, and overall business performance.

## Milestone 18: Dashboard

To begin with the dashboard setup, I navigated to the Dashboards tab within the Tours & Travels CRM application. I clicked on New Dashboard, gave it the name "Tours & Travels Dashboard", and then clicked Create. Inside the dashboard builder, I added the first component by clicking on the +Widget button. I selected the Monthly Revenue Report as the source report for this component. For data visualization, I chose the Pie Chart option, set the Maximum Values Displayed to 10, and added the subtitle “Total payments completed Bookings”. To give it a polished look, I applied the Dark Theme, then clicked Add, followed by Save.

After that, I proceeded to Activity 2, where I added three additional components to the same dashboard using the reports created during Activity 4 of the Reports Milestone. I selected appropriate charts and tables for each report, ensuring the data was presented clearly and informatively. These components offered insights into pending payments, popular travel packages, and employee role distribution—each providing valuable visual data to support business decisions.

For Activity 3, I verified the dashboard display. I accessed it by clicking the App Launcher, searched for and opened the Tours & Travels CRM app, then navigated to the Dashboards tab. There, I opened the Tours & Travels Dashboard and confirmed that it visually displayed all 4 components, reflecting the expected graphs and tables from the reports.

Lastly, in Activity 4, I created two additional dashboards using other reports from the Reports Milestone. Each dashboard focused on specific business areas—such as Booking & Payment Insights and Employee & Package Overview—helping provide better management visibility across CRM operations. All dashboards were saved in appropriate folders and structured with clear, well-labeled charts to ensure readability and usefulness.

## Milestone 19: Lightning Web Component Creation

To dynamically display travel packages based on a selected country during booking, I implemented a Lightning Web Component (LWC) integrated with an Apex Controller. First, I created an Apex class named TravelPackageController via the Developer Console. This class includes a method getPackagesByCountry, which queries all travel packages where the Country__c matches the selected input.

Next, using the Lightning Studio Chrome extension, I created a new LWC named TravelPackageSelector, exposing it to App, Home, and Record pages. In the HTML file, I designed a simple interface with a country dropdown (lightning-combobox) and a display card for the matching travel packages. The JavaScript file (travelPackageSelector.js) handles the country selection and fetches matching records from Apex using @wire-like imperative call with getPackagesByCountry.

I defined a static list of countries in the JS file for selection, and based on user interaction, the UI dynamically updates to show the available packages—without any page reload. Each package card displays important details like name, type, duration, guide availability, places covered, and more. The component metadata XML (.js-meta.xml) ensures it's accessible on different Lightning pages.

With this setup, users now have a dynamic, user-friendly interface to view only relevant travel packages based on the selected country, improving the overall booking experience.

## Milestone 20: Lightning App Page Creation

To make the Travel Package Selector component accessible within the Tours & Travels CRM app, I used the Lightning App Builder. First, I opened the org, clicked the gear icon, and searched for Lightning App Builder in the Quick Find box. I clicked New, selected App Page, and proceeded to name the page Travel Package Selector.

After clicking Next, I chose a One Region layout and clicked Done. In the builder canvas, I searched for the travelpackageselector component and dragged it into the designated region. I then clicked Save and Activate the page.

For activation, I chose Lightning Experience, selected the Tours & Travels CRM app to add the new page, and saved the configuration. Finally, I navigated to the App Launcher, searched for “Travel,” and found both the Tours & Travels CRM app and the new Travel Package Selector app page. Opening either lets users interact with the component—where they can select a country and view its associated travel packages dynamically based on previously created data.

## Milestone 21: Field History Tracking

To monitor important field changes in the Tours & Travels CRM, I enabled Field History Tracking on selected objects and fields. I began by navigating to Setup, then used the Quick Find box to search for Field History Tracking.

For the Booking object, I selected View next to it and enabled tracking. I chose to track changes on the following fields: Number of Travelers, Booking Status, and TravelPackage. After selecting these, I clicked Save to apply the changes.

Next, I enabled tracking for the TravelPackage object. Again, from the Field History Tracking settings, I searched for TravelPackage, clicked View, and enabled tracking for the fields Price Per Person and Availability Status. These changes ensure that any updates to these fields are recorded and can be viewed later in the related "History" section of the object layout.

This setup helps maintain a transparent audit trail of key booking and package details for business oversight.

## Milestone 22: Duplicate nand Matching rule

To ensure that customer entries remain unique in the Tours & Travels CRM, I configured a Matching Rule followed by a Duplicate Rule for the Customer Info object.

First, I went to Setup, typed "Matching Rules" in the Quick Find box, and clicked New Rule. I selected the object Customer Info and proceeded by clicking Next. I named the rule "Unique Email and Phone Number Combination". Under Matching Criteria, I selected the fields Email and Phone, set their Matching Method to Exact, and enabled the option "Match Blank Fields". After reviewing, I clicked Next, then Save & Activate to enable the rule.

Next, I created a Duplicate Rule. From Setup, I searched for "Duplicate Rules", clicked New Rule, and chose the same object: Customer Info. I entered the rule name "Unique Email and Phone". For both Action On Create and Action On Edit, I selected "Allow and Report". In the Alert Text, I typed: "Email and Phone must be Unique" to notify users if they attempt to enter a duplicate record.

In the Matching Rules section of the Duplicate Rule setup, I clicked Add Rule, selected the previously created matching rule (Unique Email and Phone Number Combination), and saved the configuration. Finally, I clicked Activate to enforce the rule.

This setup helps maintain data accuracy by preventing duplicate customer records based on identical email and phone number combinations.

## Milestone 23: Profile
To properly manage access and responsibilities within the Tours and Travels CRM, I created several custom profiles in Salesforce, each tailored to specific roles in the organization. I began by creating the Travel Agent Profile. From Setup, I searched for Profiles in the Quick Find box, clicked on Profiles, and cloned the Standard Platform User profile. I named the new profile Travel Agent Profile and saved it. While still on the profile page, I clicked Edit, then set the Tours and Travels CRM as the default app under Custom App Settings. I scrolled down to the Custom Object Permissions and configured the necessary access: I gave Read, Create, and Edit permissions for Bookings, Booking Guest, Booking Payments, Customer Info, and Travel Package objects. I also provided Read-only access to the Employee and Feedback objects. I saved the changes, completing the setup for this role.

In addition, I created a Tour Guide Profile by cloning the Salesforce Platform User profile. I named it Tour Guide, saved it, and edited the settings to set Tours and Travels CRM as the default app. For this profile, I only gave Read access to the Bookings, Booking Guests, and Travel Packages objects, ensuring that tour guides could view essential information without modifying data.

Next, I created the Finance Officer Profile, again cloning from Salesforce Platform User. I configured it to allow access to financial and booking data. I enabled Read, Create, and Edit permissions for Booking Payments, Bookings, and Customer Info, while giving Read-only access to Feedback and Travel Package records. This setup helps ensure financial data is visible and editable to finance personnel only.

Similarly, I created a Marketing Executive Profile, also based on the Salesforce Platform User. I granted access to Customer Info, Feedback, and Travel Packages, enabling marketing staff to access customer insights and package details while limiting their ability to modify booking data. Finally, I created a Customer Service Rep Profile that includes Read and Edit access to Bookings, Customer Info, and Feedback, allowing service agents to view and respond to customer concerns effectively.

Through this role-based profile configuration, I ensured that each user group within the organization has access tailored to their specific responsibilities, supporting data security, workflow clarity, and operational efficiency in the Tours and Travels CRM environment.

## Milestone: 24: Roles and Role Hierarchy

To define clear record-level visibility and ensure proper data access across departments, I created three new roles under the CEO role in Salesforce. These roles help establish a structured role hierarchy, making it easier to manage who can see and access specific records.

I started by going to Setup, then typed “Roles” into the Quick Find box and selected “Set Up Roles.” This brought me to the role hierarchy page where I located the CEO role.

From there, I clicked “Add Role” directly under the CEO node. In the form that appeared, I entered the Label as “Finance Officer Role”—the Role Name field was auto-filled based on the label. I then clicked Save to add the role.

Next, I repeated the same steps to add two more roles under the CEO:

First, I added the “Marketing Executive Role”.

Then, I added the “Customer Service Rep Role.”

Each role was created by clicking Add Role under the CEO, entering the appropriate label, and saving the record.

By setting up these roles under the CEO, I established a clear and scalable hierarchy, ensuring that record visibility aligns with each department's responsibilities while maintaining centralized oversight at the executive level.

## Milestone 25: Permission Set

To provide additional access to the Travel Agent Manager role in Salesforce, I started by navigating to Setup. In the Quick Find box, I typed Permission Set and selected it from the search results. Then, I clicked on the New button to create a new permission set.

I entered the label “Extra Permission For Travel Agent Manager” and clicked Save to create the permission set. Once saved, I selected the newly created permission set from the list.

Next, I went to Object Settings inside the permission set and searched for the TravelPackage object. I clicked Edit next to the TravelPackage object, scrolled down to the Object Permissions section, and enabled the permissions for Read, Edit, Create, and Delete (R/E/C/D). After updating these permissions, I clicked Save.

To assign this permission set to the appropriate user, I clicked Manage Assignments and then selected Add Assignment. From the user list, I selected the user with the Travel Agent Manager role, clicked Next, and then completed the process by clicking Assign.

## Milestone 26: Sharing Setting

To enhance data security and controlled visibility in the Tours & Travels CRM, I configured the Organization-Wide Default (OWD) and defined a custom sharing rule for the Customer Info object.

I started by going to Setup, typed "Sharing Settings" in the Quick Find box, and selected it. After clicking Edit, I located the Customer Info object and changed its OWD access level to "Private" to ensure only record owners and users above them in the role hierarchy can see the records. I then clicked Save and refreshed the page.

Next, I created a custom sharing rule to allow broader visibility for specific roles. I scrolled down to the Customer Info Sharing Rules section and clicked New. I entered the label “Customer records auto-shared with Tour Guide Role”; the rule name was automatically generated.

In Step 3, I chose to share records owned by members of Roles > Travel Agent Role. In Step 4, I specified the target users to share with as Roles > Tour Guide Role. Then in Step 5, I set the access level to Read Only, ensuring that Tour Guides can view the customer records but not edit them.

Finally, I clicked Save to activate the sharing rule, allowing secure and role-based access to Customer Info records.

## Milestone 27 -Test Classes

To ensure the correct functioning of the BookingTrigger and BookingTriggerHandler logic, I created a dedicated test class called BookingTriggerTest. This test class verifies that when a new booking is inserted, related records for payment and booking guests are automatically created with the correct values. The test not only validates automation logic but also ensures Apex code coverage required for deployment.

I began by logging into Salesforce with administrative privileges. From the top-right gear icon, I accessed Setup, then launched the Developer Console. Inside the console, I clicked on File > New > Apex Class and named it BookingTriggerTest.

In the test method, I first inserted a sample Customer_Info__c record with test data, including the Date of Birth, which was a required field. Then I created and inserted a Travel_Package__c record, making sure to fill all mandatory fields such as Country__c, Price_Per_Person__c, Duration_in_Days__c, and Places_Covered__c.

Next, I created a Booking__c record. I populated important fields like Number_of_Travelers__c, Booking_Status__c, and linked it to the travel package and customer created earlier. I also ensured the Booking_Date__c field was filled to avoid validation errors.

After inserting the booking inside a Test.startTest() and Test.stopTest() block, the trigger logic fired. To confirm that the trigger and handler performed as expected, I queried for the related Payment__c record and asserted that it was created with a default status of "Pending". I also validated that the correct number of Booking_Guest__c records (three, in this case) were generated and named appropriately (e.g., "Guest 1").

This test ensures the booking automation logic functions correctly and provides sufficient code coverage for deployment readiness. Once the test was saved, I ran it and confirmed that it passed without errors.
