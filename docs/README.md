[![Build Status](https://dev.azure.com/accountgo/accountgo/_apis/build/status/AccountGo-Nightly-Build)](https://dev.azure.com/accountgo/accountgo/_build/latest?definitionId=10)

# AccountGo
Accounting System built on DOTNETCORE, an opensource and cross platform (ASP.NET + ReactJS on the Frontend). It's in early stage and still lots of work to do but happy to share it to anyone. This will be very useful if you have future project to develop accounting system. We do the hard work for you!
It is initially designed for a small size businesses and the idea is to help them running efficient business by using Accounting System fit to them.

### IMPORTANT NOTE:
You can completely use MacOS, Linux, Windows to develop and deploy this project.

We envisioned this project will be ported to microservices architecture and using kubernetes. Perhaps some microsevices will be coded in F# for functional programming and machine learning.

# Features
On a high level, this solution will provide modules including

1. Accounts Receivable
2. Accounts Payable
3. Inventory Control
4. Financial/Accounting

# Setup Development Environment (Visual Studio Code)
AccountGoWeb and Api projects are using ASP.NET Core 2.1.

-   “AccountGoWeb” requires webpack, webpack-cli, gulp, typescript installed
-   “Api” – ASP.NET REST API project to be consumed by “AccountGoWeb”

1. Install Visual Studio Code.
1. Clone/Fork the latest repo here https://github.com/AccountGo/accountgo
1. Build each projects in this order. Core->Services->Dto->Api. To build the project, change directory to project folder, execute "dotnet restore" then "dotnet build". Make sure all projects build successfully. Alternatively, use accountgo.sln file to use by dotnet build. To do this change directory to "src" folder, execute "dotnet restore", then "dotnet build".
1. AccountGoWeb require more steps to completely build the front-end artifacts. To do this, follow the succeeding steps.
1. Change directory to src/AccountGoWeb and open Visual Studio Code terminal.
1. Install typescript by executing"npm install -g typescript".
1. Install webpack-cli by executing "npm install -g webpack-cli".
1. Install webpack by executing "npm install -g webpack".
1. Install gulp by executing install -g gulp".
1. Still in the same folder, type and enter the following in command prompt.
1. "gulp" (This will run the gulpfile.js)
1. "tsc" (This will run the tsconfig.json)
1. "webpack" (This will run the webpack.config.js)
1. And lastly, in src/AccountGoWeb terminal, execute "dotnet build"
1. To test if the front-end build successfully, in src/AccountGoWeb terminal, execute "dotnet run"
1. To test if the backend api build successfully, in src/Api terminal, execute "dotnet run"

### IMPORTANT  NOTE:
Your wwwroot folder should be look like this if you correctly followed the steps above

![AccountGo](https://user-images.githubusercontent.com/17961526/45582820-273d0000-b8e9-11e8-9ff0-2b3f8f978513.png)

Next, setup database and backend api database connection

# Setup SQL Server (Using Docker)
You can opt to install SQL Server or use docker image (like we do). Assuming you have docker installed, follow the steps below. (Install docker if you haven't done)
1. Open command prompt (terminal for MacOS).
1. Execute "docker pull microsoft/mssql-server-linux". We prefer to use SQL Server for Linux for lightweight.
1. Run sql server for linux. 
1. Execute "docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Str0ngPassword!' -p 1433:1433 -d --name=local_mssql microsoft/mssql-server-linux"
1. Download SQL Operation Studio by Microsoft to manage the SQL Server. https://docs.microsoft.com/en-us/sql/sql-operations-studio/download?view=sql-server-2017
1. Open SQL Operation Studio and connect to your running SQL Server docker container.

# Publish Database
This requires improvement for easy deployment and initialization. This instruction is old which uses Visual Studio instead of Visual Studio Code.
1. Open solution in VS. The SQL Database project is under Database\SQL.Accountgo
2. Right click the project Database\SQL.Accountgo and select Rebuild.
3. Right click the project Database\SQL.Accountgo and select Publish.
4. In "Target database connection", click "Edit" button.
5. Select existing database connection or create a new one.

# Run "Api" project
1. Run the api by typing "dotnet run". Make sure you change directory to src/Api
2. In api/appsettings.json, update properly your "LocalConnection" connection string.
3. In api/Startup.cs, then ConfigureServices method, set connectionString = Configuration["Data:LocalConnection:ConnectionString"];

# Run "AccountGoWeb" Front-end
1. Run the frontend by typing "dotnet run". Make sure you change directory to src/AccountGoWeb

# Initialize Data
On your first run, if you successfully Publish Database\SQL.AccountGo you will get an empty database. Let's get your DB Initialized with sample master data.'
1. Create your first user. registration page is hidden but you can go directly from your browser. (e.g. http://localhost/account/register)
2. Set password like 'P@ssword1'. More than 6 chars, 1 Caps, 1 special, 1 number. Note: Currently, even successfully register a new user, it will not inform you. Just try to login using your newly created user. This registratio page is temporary.
3. After successful user registration, the system automatically runs data initialization of the following.
- Company
- Chart of accounts/account classes
- Financial year
- Payment terms
- GL setting
- Tax
- Vendor
- Customer
- Items
- Banks

# Front-end
The screenshot below will be the future front-end. It is heavily under-development and you could be part of it. The project is "AccountGoWeb" and consuming the "Api" project.

Technology Stack:
- ASP.NET Core
- ReactJS
- MobX, React-MobX
- Axios
- Bootstrap
- D3
- React-router (on some pages)

Demo site (new UI) : http://accountgo.net

![accountgoweb](https://cloud.githubusercontent.com/assets/17961526/17953180/d2e7aac2-6aa3-11e6-8150-fe1b8274cf91.png)
![accountgoweb](https://cloud.githubusercontent.com/assets/17961526/17430653/0cf89cca-5b28-11e6-81dd-5f14695c8cfc.png)
             

# Help Wanted
Wether you are a Developer, Consultant, Accountant, QA, Marketing expert, Project Manager we can all be part of this great and promising project.

If you are a developer and wanted to take part as contributor/collaborator we are happy to welcome you! To start with, you can visit the issues page and pick an issue that you would like to work on.

So go ahead, add your code and make your first pull request.

# Contact Support
Feel free to email mvpsolution@gmail.com of any questions.