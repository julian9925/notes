---
id: 7r5iumr1gtuyikis6je11rz
title: Summary
desc: 'ThingWorx Document Summary'
updated: 1699343574977
created: 1699320581058
---

# Day 1 Intorduction

## 1. Overview
  For application development through modeling rather than coding, focusing on agility and application composition.

## 2. Advantage
  The platform offers benefits such as faster time to market, simplicity, a single platform for development, and built-in analytics.
	
## 3. Following ISA S95 Model
![](/assets/ISA-S95-architecture.png)


## 4. ThingWorx Capabilities
- Role-based consoles
- Language translation services
- Pre-built extensions
- Connectivity with shop floor devices through Kepware
- Monitoring and alert management
- Dashboards and reporting
- ThingWorx Analytics
- SSO for third-party applications
- Easy access to AR/VR technology via Vuforia studio

## 5. ThingWorx Prerequisites
 - Compiler
   - JDK
	

 - Web server
   - Apache Tomcat


 - Database
   - PostgreSQL
	 - MS SQL Server


 - Data Service
	 - SAP HANA
	 - DataStax Enterprise

## 6. Models in ThingWorx
  -  modeling
	- analytics
	- visualization
	- data storage
	- collaboration
	- security
	- system management

## 7. ThingWorx Composer 
  - Integrated development environment (IDE) for creating ThingWorx applications, with both data modeling and user interface development capabilities.

- IDE snapshot
![](/assets/thingworx-composer-homepage.png)


- Data Analysis Definition
![](/assets/data-analysis-diagram.png)

  Once created DAD, using API call analysis request and wating analysis process done.

- Mashups and Reports in Thingworx (Data Analysis)

  - Drag and drop widget
	- Connect database
	- Writing code snippet to fetch data (Javascript/SQL)
	- Bind data to your chart/grid
	- View your mashup

- New Composer Features

  The NEW button for creating entities, the Browse Navigator for accessing entities, and the Recent tab for accessing recently used entities.

- Documentation and Change Tracking

  - The Classic Composer has a Save button that allows users to add comments describing changes
	- Each entity has a Change History page to track changes and comments.



## 8. Kepware server with ThingWorx
![](/assets/kepware-service.png)

- Kepware advantages
  
	- Industrial connectivity streamlines data integration from common operational systems such as MES, SCADA, PLCs, and CNCs.
	- It creates a scalable and repeatable architecture for data handling.
	- Manufacturers can maximize the utility of machine data by making it actionable.
	- Simplified connectivity reduces maintenance needs and machine downtime.
	- It helps ensure that equipment meets compliance standards.


# Day 2 Thingworx modeling/visualization

## 1. Modeling
- Create a sample Thing
- Configure your Thing to connect the Database
- Write a sample service to fetch a table from database
- Create a Data Shape



## 2. Create Thing and connect to Database

### **connect to database**

- Access the 'Projects' menu from the right sidebar.
- Click on the 'New' button to create a new project.
- Access the 'Things' menu from the right sidebar.
- Click on the 'New' button to create a new Thing.
- Enter a name for your Thing.
- Choose an appropriate Thing Template from the list provided.
  (For connecting to an MSSQL database, use the MSSQLServer template)
- Navigate to the configuration menu of the Thing you created.
- Enter the database details in your JDBC Connection String, formatted as follows: `jdbc:sqlserver://localhost;databaseName=<yourDatabaseName>`.
- Enter the credential information to connect to the Database

### **Present the table query result**

- Go to the services menu of the thing you just created
- Click on "Add my service" button.
- Select the service type as SQL Query, which is used for querying a table from the database.
- Name your service and write your code.
- Click on "Save Entity".
- Test the service by clicking on "Test" and then "Execute query" in the popup to ensure the code works as expected.
- Click and create Data shape after your service get successfully executed.

![](/assets/table-query-result.png)

### **Creating a DataShape**
- Name your data shape and link it to the project created.
- Link the created datashape into to the service written in the Thing.

![](/assets/create-DataShape.png)

### **Adding services to mashup**
- Click on the 'Mashups' menu from the right sidebar.
- Click on the 'Create New' button to start a new mashup.
- Search for the grid widget in the widget section.
- Drag and drop the grid widget onto your mashup.
- Click on the '+' icon in the data section.
- In the popup that appears, search for the Thing you created earlier.
- Select the service from the Thing.
- Check the 'Mashup Loaded' checkbox and click 'Done'.
- Drag and drop the 'all data' onto the grid.
- Save the mashup.

### **View Mashup**
- Click on View Mashup to view the mashup in design time.

![](/assets/view-mashup.png)

# Day 3 Thingworx entities Part. I

## 1. Agenda

- Security
  - Create a user
	- Create a user group
	- Create an organization


- System
	- Localization table


- Configuring visibility, design time and run time permissions

## 2. Create a User Group
- Click on the user group menu under security tab
- Enter the user group name
- Click on save

![](/assets/create-user-group.png)

## 3. Adding users/member to a User Group

- Click on the Edit Members button
- In the popup that appears, drag and drop the necessary members and click on save.
- After the popup close make sure to
Save the group once again

![](/assets/assign-user.png)

## 4. Create an Organization

- Click on the organization menu
from the right side bar under
security tab
- Enter the name of the
Organization
- Click on change button for login
image
- Choose an image file from your
local to set the Image for the login
page.
- Choose the mashup you want to
display post successful log in in the
Home Mashup

![](/assets/create-organization.png)

## 5. Adding units and members to an Organization

## 6. Setting Visibility for users/user groups

- Go To the Visibility menu on your Thing and Mashup
- Click on ”Add Org/Org Units” button
- Search for the Organization we created in the previous step and select any unit and click done

![](/assets/setting-visibility.png)

## 7. Setting Design Time permission for users/user groups

- Go To the Design Time menu on your Thing and Mashup
- Search for the User or user group we created in the previous steps
- Click on the green icon to enable the Read, Update, Delete options

## 8. Setting Run Time permission for users/user groups
- Go To the Run Time menu on your Thing and Mashup
- Search for the User or user group we created in the previous steps
- Click on the green icon to enable the Property Read, Property Write,
Event Execute, Event Subscribe
and Event Execute

## 9. Logging into the developed Thingworx Application
- Hit the URL
http://localhost:<yourPortNumber>/Thingworx/FormLogin/<organization_name>
- Enter a valid Username and Password
- Click on Submit

(Wrong snapshot??)

# Day 3 Thingworx entities Part. II

## 1. Agenda


- Security
  - Create an Application Key


- Kepware configuration to connect to
Thingworx
- Creating Things to log tag values from
kepware
- Displaying Kepware tags values on Mashups

## 2. Create an Application Key
- Click on the Application key menu from the right side bar under security tab
- Enter a name for the application key
- Set the Expiration date as required
- Add the User Name Reference as Administrator
- Click on the Save button

## 3. Create an Industrial Gateway Thing
- Create a Thing with Thing Template as Industrial Gateway

## 4. Kepware configuration to connect to Thingworx
- Open Kepware
- Load your .opf project file into thingworx
- Right click on Project and go to Properties

![](/assets/kepware-config.png)

- Click on thingworx
- Change the Enable field to yes under the Server Interface
- Give your Tomcat server Host and Port details
- Copy the application key created in the Initial step and paste it in the Application key section
- Change the Disable encryption field to yes under connection settings
- Give the Thing Name of type industrial gateway created in the
initial steps

![](/assets/kepware-property.png)

## 5. Creating Things to log tag values from kepware

- Click on the New composer on the Thingworx header section
- Open the created Industrial gateway thing and click on Discover tab
- Browse for the channel and device name
- Choose all the Tag names required
- Click on Bind to new Entity
- Choose Remote Thing in the popup that appears, Click OK
- Give a name for the Thing
- And Create a new value stream and map it to this thing

![](/assets/log-tag-value-from-kepware.png)

- Click on properties and Alerts in the Remote thing we created
- Click on each property and check the Logged Base type
- Click on save

![](/assets/kepware-alert-properties.png)

## 6. Displaying Kepware tags values on Mashups
- Switch to the old composer view
- Go to the Remote thing created in the Previous step
- Go to the services menu
- Test the QueryPropertyHistory Service
- Create a Datashape from the Service result and save it

![](/assets/entity-services.png)

- Choose the Mashup in which the kepware tags need to be displayed

![](/assets/entity-mashups.png)