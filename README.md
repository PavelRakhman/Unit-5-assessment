# Unit-5-assessment
Assessment 5 attempt 2

For this assessment, I used the MySQL dialect and MYSQL Workbench to view changes in the database. To run and test the assessment, you will need to install MYSQL Workbench and create a schema with the following configuration:
Host: localhost
Username: root
Password: CromFeyr198862!
Port: 3306
(These parameters are already included in my config.json file)

I also decided to recreate the front end. The user can add entries to the database, but instead of typing in the name of the city, the user will need to select a country and its capital. The reason why I did this was to prevent the user from adding non-existent countries
When the window loads, a get request is sent to the server. The server gets all countries and appends their names to the select menu. Once the user select a country, another request is sent to the server. The server now searches a capital by the country id and appends the capital name to the second select menu. The user can also specify the date when they visited the capital. When the user clicks add entry, all data from the form is converted into an object and sent to the server, which adds it to the database.

Tables included in the database: 
countries
capitals
tj (stands for travel journal)
Type of association between these tables: one to one (one capital has one capital)
The tables are stored in the folder called models. Connection to the database and associations are established in the index.js file, which is also stored in the models folder

To create these models, I followed these steps:
1)npm install –save-dev sequelize-cli
2) npx sequelize-cli init
3) used sequelize.define(“model name”, {attributes}) method (in the index.js fiel in the models folder)

Seeding the database
The dummy data used to seed the database is stored is separate files in the DaataArrays folder and exported
How seeder files were created
First, I created a seeder file for each of the folders by typing in the following commands in the terminal:
npx sequelize-cli seed:generate –name countries-seeder
npx sequelize-cli seed:generate –name capitals-seeder
In the seeder files, I used queryInterface.bulkInsert and bulkDelete – methods to tell te program what to insert into and what to deket from the models. Once seeder files were created, I typed the following command in the terminal:
npx sequelize-cli db:seed:all

Controllers and routers
There are three controllers in this assessment:
countriesCtrl.js (used for sending the names of countries from the database to the front end)
capitalsCtrl.js (used to send names of capitals from the database to the front end)
entryCtrl.js (used for adding entries to and getting entries from the database)
These controllers are imported in the router files and used in app.js
