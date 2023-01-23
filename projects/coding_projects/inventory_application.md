# Inventory Applicaiton

### Purpose
The purpose of the application is complete the goal of creating a IOS application. The purpose of the project was to test allow for a inverntory management system for a homeowner. We do not lost track of where things are stored. The application can also be purpose for performing inventory in the 

### Technologies

- React Native
- Firebase authentication
- FireStore database
- App Deployment (Apple & Google playstore)


### Functionality 

- Lets user log items and tag their location 
- User can search the inventory for the items
- There is a QR functionality with the application

### Data Models

User
- Name
- Email

Item
 - owner (user)
 - price (dollars)
 - location (String)
 - status (boken, working, inrepair)
 - QR Code (Optional)
 - Data Logged (Hidden)


#### Screens

###### App Screens
Main Screen Page
- Search Items in a search bar
    - By Name
- Shows all itmes in a list of Items
    - Name
    - Price
    - State
- Add Item Button
    - Propers up a from for adding the item

Add Item Screen
- Form to enter Item info
    - Name Required
    - Type Optional
    - State Optional (default working)
    - Price Optional (default 0)
    - Location Optional
    - Pictures Optional
    - Description Optional
- Add Item botton
    - Only enable when entry in entered

View/Edit Item Screen
    - Edit Screen

Setting Screen
- Shows Email
- Log out

Filter Screen
- Price Range
- Status Types
- By location 


## Requested Features
- bar code scanning
    - Purpose of the using the bar is to make it quick and easy to enter the items
    - Any kind of identification that can be used to identify the item
    - Book ISBN number
    - Computer Items UPC code
    - they are scannable using the binary code
    - 
- Add a barnd field optional
- Should be able to create a listing
    - LetGo
    - Cregslist
