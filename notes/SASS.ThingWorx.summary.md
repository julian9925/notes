---
id: 7r5iumr1gtuyikis6je11rz
title: Summary
desc: 'ThingWorx Document Summary'
updated: 1699328008654
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
- lick on the 'Mashups' menu from the right sidebar.
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