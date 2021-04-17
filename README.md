# contractManagement
A scriptable-app script to manage the appointments and payments of your contracts in your calendar and task manager / todo-list. It comes with a widget and can also be used for insurances, ID-cards, vaccination dates and more.

Did you ever pay too much for your cell phone contract because you forgot to quit in time?

Here is the solution. I proudly present a scriptable-app script for contract-management.
It manages the appointments of your contracts (notice period, preparation period) the payments (monthly, yearly) and has a widget that show your upcoming contract projects. The script can be used for
-	Contracts
-	insurances
-	Vaccination dates
-	ID-cards
-	Credits
-	Medical examinations
-	Recertification of qualifications
-	Lease rental charges and extra costs

Features
========

The tool has the following features:

Appointment-Management
-----------------------
This is the core competence of the script. A contract has an expiration date and a notice period. To quit the contract in time you may also need preparation time. Think about your cell phone contract. The contract may end Mai 1st . But if you don’t quit 3 months ahead the contract gets extended automatically (typically with a worse price). Just to quit an February 1st doesn’t help too much since you may need preparation time to find a better deal or negotiate with your provider. Let’s say you need two weeks to prepare the quitting.
Now let the contract manager support you! The script writes the expiration date of your contract into your calendar and creats a task/reminder in your task manager. I use the 2Do-App for the latter since a task within the 2Do-App has a start and a due date. Two weeks before the deadline (expiration date minus notice period) of your cell phone contract the task with pop up in your task manager.
So the simple feature is to have a task in your reminder app and an event in your calendar for each contract. However, I soon realized that this appointment-management is useful for more objects than just contracts. I also use it to manage the ID-cards, vaccinations, medical examinations and recertification of some licences for the whole family.

Gant-Charts
-----------
To have a better overview about the appointments they are shown within a Gant-chart: To lines on a time axis, the first for the preparation period and the second for the notice period. The Gant chart is shown in the widget with all contract-projects and also for each entry individually

Payment-Management
------------------
When starting to collect the information about my contracts I also was trying to get an overview about the costs. So I also entered the rates and the payment intervals (monthly, each quarter, half-yearly, yearly) into the data base. A bar chart shows the payments for each month a year so you can see an expensive month coming in time and tighten your belt.

Widget
------
A widget shows the most important information about all your contracts/entrys. You can see upcoming events, upcoming dates, a gant-chart for all your contract-projects, a bar chart with the monthly costs and information about your average and actual payments.
Input-Mode with filter
When you start the app (not in widget mode) you can add or change your contracs. A table gives you an overview about all contracts. You can select one for more details. But you can also filter the table according to any criteria. I find it useful to filter the contracts with respect to the owner. So I can see which kid costs the most 😊. Also useful is to filter according to the entry type: When are the next vaccinations necessary? When do we need new passports?

Templates for the contract details
----------------------------------
When you enter a new contract/entry you can select the predefined keywords. So you don’t have to type too much. You can easily select the owner from a list, the precise wording in the calendar event and so on. Of course, you can also create your own terms.

Requirements
============
-	2Do-App
-	Sync process between 2Do-App and the iOS native reminders-App
Installation
-	Copy the script to scriptable and rename it contractManagement
-	Copy the contractsMetaData.json to a folder on your iPad/iPhone
-	Copy the contracts.json into the same folder
-	Create a “File Bookmark” of the folder within the scriptable app. Label the Bookmark and replace the standard File Bookmark “syncVerzeichnis” in the script with your label
-	Optional: I recommend to create a new list within the 2Do app for the contract-management
-	Enter the name of the used list within the 2Do-App 
-	Enter the name of the calendar for the expiration dates 
-	Create a new scriptable-widget which executes the contractManagement. I designed the script for a large widget. Also medium-size is supported.

Known limitations
=================
I use the 2Do-App to manage tasks since the tasks have a start date and a due date. Feel free to add an interface for other task-manager like fantastical, wonderlist, … and share it here. So fore you need it as a prerequirement. However, the 2Do-App has a limitation. The results of a search are only shown within the app and are not returned via x-callback-URL. For searching the tasks if a task already exists I therefore use the reminder-app. 
When you have entered a new contract and the task is added to the 2Do-App you need to sync the iOS native reminder-app with 2Do and you need to push the sync process manually. Otherwise the the task will be added again since it can’t be found within reminders.
Events are only added to the calendar app when the date is less than one year ahead. This is a limitation of iOS which only syncs the calendar for one year.
Tasks are only added when the task is not more than three years ahead. This is also a limitation of iOS. Only task up to – I think it was 4 – years are downloaded from the server.
Whenever you enter a contract it is saved and the sync-process is executed. This also happens even when no changes were made.

Ideas for improvements
======================
You could add new parameters to a contract. E.g. 
-	the folder within your file system where the files of the contract is stored (phone bills). When pressing the button the contract opens as PDF.
-	you could add a URL to the contract provider for quick access to further information or a login
-	you could add a link to a contact in your address book.
Support for starting the script with parameters. As one parameter the ID of a contract could be given. 
-	The widget could become interactive. There could be a link within the widget to the contract. The link opens the contractManagement-script with the contract ID as parameter
-	Also, there could be a x-callback-URL link in the notes part of a calendar event or reminder which starts the contractManagement with the contract-ID as parameter
Languages:
-	Currently, everything is in German.
Export function of the database to:
-	Datajar
-	csv

Tools for simplification when using several devices
===================================================
I assume that calendar and reminders are in sync when you use the contractManagement. You may also want to share the contracs.json-Database. I therefore created a simple scriptlable-widget-script which shares files between several iOS/iPadOS devices whenever pushed. You can find it here:

Widget for synchronization of folders between iOS and Server (WebDAV, SMB) - Scriptable - Automators Talk
https://talk.automators.fm/t/widget-for-synchronization-of-folders-between-ios-and-server-webdav-smb/10555/8

History:
========
This is my third attempt to create a contract management. 
1. The first version was made for iOS shortcuts app with a csv as database. But that didn’t work.
-	The shortcuts script got too long and the shortcuts database crashed due to some bugs of the shortcuts app. So I had to restart as all shortcuts got lost.
-	The idea of the csv was to have the payment management in Excel. But converting csv to json and vice versa became too slow with 50 contracts
2. The second version was also based on shortcuts with a lot of sub shortcuts and DataJar as database. That works OK but had no widget
3. This is the third version and my first version for scriptable. The database is a json-file. I like the widgets. I still would prefer datajar as database but it has no interface for scriptable-app. 
