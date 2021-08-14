## A financial managing and tracking Android app with Ktor backend
This project was my thesis for my Master degree. I wrote both the mobile app and backend in **Kotlin**. I made it in MVVM architecture with dependecy injection (**Dagger 2**).
The code is private, here I just share the details about the project.

### Features
* **Registration, login, logout**
 
The user can create an account and use that. The server can handle more accounts.

<img src="https://user-images.githubusercontent.com/37157607/129448018-b4ddb021-69ee-49af-8ae5-bfa8cc2736f7.gif" width="265" height="574">

* **Home screen**

At the top the user can see his/her total money. Below that the widget shows the total money of each day of the actual week. The logout button is in the profile page.

<img src="https://user-images.githubusercontent.com/37157607/129447999-3b91fef1-a474-4131-ba0e-5a0dab01f11b.gif" width="265" height="574">

* **Goals, savings**

The user can create goals to save money. For example for a new bike the user can create a goal. He/She should set a deadline and a goal amount to collect. By clicking the add money the app will track the saved amount and add it to the transaction list also.

 <p>
    <img src="https://user-images.githubusercontent.com/37157607/129447933-731528ea-5c08-4e88-81ae-53f1ea464e99.gif" width="265" height="574">
   <img  width="10" height="1" src="">

   <img src="https://user-images.githubusercontent.com/37157607/129447979-ebab88fe-b340-4016-aca1-5a5ca85d5886.gif" width="265" height="574"> 
   <img  width="10" height="1" src="">

 </p>
 
* **Lists transactions**

Transaction types: income, expense, saving. The list groups the transactions by day. It shows the most important data of the transactions. The transactions are deletable by long click. 

<img src="https://user-images.githubusercontent.com/37157607/129448970-485cba71-cef8-4d50-9e7f-f8862e41eec6.gif" width="265" height="574"> 

* **Create a transaction, detials page**

A transaction contains elements. By adding categories to these elements the user can get more detials in charts. The user can set the name, date, time, main categories, add/scan/delete elements. For the elements he/she can set the name, price and subcategory. I made the app to be smart so when the user selects a subcategory, the app automaticly adds its parent category to the transaction's main category list. Also if there is a lot of element we can hide the top part of the screen to see just the elements.

 <p>
   <img src="https://user-images.githubusercontent.com/37157607/129448150-f0737019-f584-4c2f-90e4-8032e660c70a.gif" width="265" height="574">
   <img  width="10" height="1" src="">
 
   <img src="https://user-images.githubusercontent.com/37157607/129448074-ed432ba8-de1b-4351-97af-552361dfd972.gif" width="265" height="574"> 
   <img  width="10" height="1" src="">
 </p>


* **Scan receipts by OCR**

Here the user should scan the receipt. The app will recognize the text and write it in the screen. The user can click on the matching name and price to fill the input fields at the top. If the recognition was not proper he/she can correct it by hand and then add it to the list.


* **Create/delete main or subcategories**
 
This category system has a parent-children hierarchy. I designed this system to be able to make more precise analysis. Main categories are for the transactions and the subcategories only for the transaction elements. The app handles the category deletion too. It checks the database and deletes them from the previously added and saved transactions too.
 
 <p>
   <img src="https://user-images.githubusercontent.com/37157607/129448036-3304a874-ca4a-4afe-ade3-dc247d0da138.gif" width="265" height="574">
   <img  width="10" height="1" src="">

   <img src="https://user-images.githubusercontent.com/37157607/129448908-287bc44b-597d-43a7-86c5-d18ca2e850e3.gif" width="265" height="574"> 
   <img  width="10" height="1" src="">
 </p>

* **Charts**

The charts are very useful. I show a lot of information on that page. The first widget is a short summary about total money, goal status and the actual month and week data.

The next widget is about expense and income. The interval is selectable it can be a year, a month or a week. The user can change these intervals fastly by clicking the arrows or choose it with the date interval selector page. The x axis shows the days the y axis shows the money amount. With the button in the bottom right corner the lines in the chart can be turned off one by one. Also the chart is zoomable in both direction.

The last widget shows information about the categories. The interval selection and changing is the same here as in the previous. Here there is 3 mode: categories by usage, by expense, by income. I did a condition to only show value numbers in the chart if they are big enough because otherwise they overlapped. Below the chart the collected data is visible. For the main categories the percentage is applies to total amount in the selected interval. For the subcategories it applies to the total amount for its parent category.


 <p>
   <img src="https://user-images.githubusercontent.com/37157607/129447896-f82f2dc8-1918-4f11-ae93-afec75c2485e.gif" width="265" height="574">
   <img  width="10" height="1" src="">

   <img src="https://user-images.githubusercontent.com/37157607/129448641-cdde3354-8da3-4719-9b90-cac2eb965a93.gif" width="265" height="574"> 
   <img  width="10" height="1" src="">
 
   <img src="https://user-images.githubusercontent.com/37157607/129448119-cc601a2d-256e-4e91-9d39-d520e410f815.gif" width="265" height="574">
   <img  width="10" height="1" src="">
 </p>


* **Revoult like date interval selector**

For the charts I did a date interval selector screen. I made the design based on Revoult's date selector page. I made it reusable. In the future I planning to create a library about it with more features. The user now can select a year, a month or a week. It shows the actual date in all of the 3 pages. The pageing is smart. For example in the month page it can happen that a few days are visible from the next month. If these days are clicked the month interval automatically jumps to that month. Also the user can set everything to the defaults which is the actual date.

<img src="https://user-images.githubusercontent.com/37157607/129448846-3d983bd0-a02b-4b6b-9556-ddad1792d6ea.gif" width="265" height="574">

* **Transparent statusbar, custom navigationbar**

In Android it's hard to create a transparent statusbar. I did a trick. I draw the activity to the whole screen without the statusbar and then set the proper padding to the root layout to be under the statusbar. To get the actual size of the statusbar I set a window insets listener. From that I will get the height of the statusbar which is important because there is a lot of device with different notch at the top. 

I did a custom navigationbar. To its top I made a smooth gradient. This is visible when there is a scrollable content.

* **Communication with the backend, local database**

The app refreshes its database on every login and app start. Also it documents every changes in the server first and then if it was successful the app does it too.

* **JUnit tests**
 
I did a few JUnit tests also. The dependecy injection came in handy there too.

* **Fragment Navigation Pattern with centralized navigation**

I used the Navigation library from the Jetpack and I centralized all navigation methods into one class. Also I followed the fragment navigaiton patter so there is one Main activity and the pages are fragments in this activity. For screens that are logically too different I used individual activity: scanning, date interval changing, category selection/editng.

### Used third party libraries
**Mobile app**
* Kotlin
* ABBYY Real-Time Recognition SDK
* MPAndroidChart
* Room Persistence Library
* Dagger2
* Navigation component
* Kotlin Coroutines
* Retrofit
* ConstraintLayout
* Material components
* LeakCanary
* JUnit

**Backend**
* Ktor
* Kotlin
* Hikari
* Beekeeper Studio
* PostgreSQL
