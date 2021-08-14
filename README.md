## A financial managing and tracking Android app with Ktor backend
This project was my thesis for my Master degree. I wrote both the mobile app and backend in **Kotlin**. I made it in MVVM architecture with dependecy injection (**Dagger 2**).
The code is private, here I just share the details about the project.

### Features
* **Registration, login, logout**
 
The user can create an account and use that. The server can handle more accounts.


* **Home screen**

At the top the user can see his/her total money. Below that the widget shows the total money of each day of the actual week. The logout button is in the profile page.

* **Goals, savings**

The user can create goals to save money. For example for a new bike the user can create a goal. He/She should set a deadline and a goal amount to collect. By clicking the add money the app will track the saved amount and add it to the transaction list also.


* **Lists transactions**

Transaction types: income, expense, saving. The list groups the transactions by day. It shows the most important data of the transactions. The transactions are deletable by long click. 

* **Create a transaction, detials page**

A transaction contains elements. By adding categories to these elements the user can get more detials in charts. The user can set the name, date, time, main categories, add/scan/delete elements. For the elements he/she can set the name, price and subcategory. I made the app to be smart so when the user selects a subcategory, the app automaticly adds its parent category to the transaction's main category list. Also if there is a lot of element we can hide the top part of the screen to see just the elements.

* **Scan receipts by OCR**

Here the user should scan the receipt. The app will recognize the text and write it in the screen. The user can click on the matching name and price to fill the input fields at the top. If the recognition was not proper he/she can correct it by hand and then add it to the list.


* **Create/delete main or subcategories**
 
This category system has a parent-children hierarchy. I designed this system to be able to make more precise analysis. Main categories are for the transactions and the subcategories only for the transaction elements. The app handles the category deletion too. It checks the database and deletes them from the previously added and saved transactions too.

* **Charts**

* **Revoult like date interval selector**

* **Transparent statusbar, custom navigationbar**

* **Communication with the backend, local database**

The app refreshes its database on every login and app start. Also it documents every changes in the server first and then if it was successful the app does it too.

* **JUnit tests**
* 
I did a few JUnit tests also to try it out. The dependecy injection came in handy there too.

* **Fragment Navigation Pattern with centralized navigation**

I used the Navigation library from the Jetpack and I centralized all navigation methods into one class. Also I followed the fragment navigaiton patter so there is one Main activity and the pages are fragments in this activity. For screens that are logically too different I used individual activity: scanning, date interval changing, category selection/editng.

### Used third party libraries
* Kotlin
* ABBYY Real-Time Recognition SDK
* MPAndroidChart
* Room Persistence Library
* Ktor
* Dagger2
* BeeKeeperStudio(?)
* Prs valami SQL
