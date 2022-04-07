# Configuring AppSignal with NodeJS

Code insights allow developers to re-think their solution and enable them to scale products from hundreds to millions of users. Life can be a lot easier if you know which part of your code is a resource gobbler. If you are looking to scale you application for the masses, we have got you covered. With AppSignal we provide in depth insights on your code, platform and identify the processes that can be improved. 

AppSignal can be integrated into various kinds of applications i.e., Ruby, Elixir, NodeJS and JavaScript. We prefer a seamless integration experience where you can focus on improving your code rather than configuring application insight tools. Hence, our installation and configuration process are extremely simple. 

This guide will take you through the process of integrating AppSignal in a NodeJS application. I am going to use a very simple NodeJS application that retrieves data from blockchain. You are welcome to use any NodeJS application of your choice as the steps described below apply to all NodeJS applications. Follow these steps to successfully integrate AppSignal with your NodeJS app. The steps are:
1.	Creating a Free account on AppSignal
2.	Configuring your NodeJS Application
3.	Executing your application
4.	Checking out AppSignal’s Dashboard

## Prerequisites:
To complete this guide, you need a NodeJS application, a supported environment, see [supported operating systems](https://docs.appsignal.com/support/operating-systems.html#main), and a package manager i.e., npm installed on your system. You would also need a text editor for editing your JS files. For this guide, I am using _Ubuntu 20.04.4 LTS_, _Visual Studio Code_, and latest versions on _NodeJS_ and _npm_.
### Creating a free account on AppSignal
AppSignal allows developers to create a free trail account for them to experience the power of AppSignal’s solution. Click [here](https://appsignal.com/users/sign_up) to Signup.
 -	Once you sign up, you can either [Join your team](https://docs.appsignal.com/organization/team/teams.html#main) or [Create new organization](https://docs.appsignal.com/organization/#main) on the AppSignal’s dashboard.
 - After creating or joining your team, you’ll see the **Choose your language** screen. You can choose an option depending on your project's needs.

![image](https://user-images.githubusercontent.com/13951043/162156944-62fb56f5-18aa-49af-9fab-b8f54fab46dc.png)

### Configuring your NodeJS application
Since we will be configuring AppSignal for a NodeJS application. Let's select the _Install for Node.js_ option. As a result, you'll be redirected to the **Install AppSignal** page.

![Screenshot 2022-04-07 151055](https://user-images.githubusercontent.com/13951043/162176373-cab2acd0-09f2-4580-8a5e-260ea37ab823.png)

- The installation of AppSignal into any node project requires two things: the _AppSignal library files_ and a _Push Key_. We will need to add both to our NodeJS project so let's do that. Open your project folder in a text editor.
- Inside the project directory, open a terminal window. You can use the built-in terminal window in Visual Studio Code.
- Copy & Paste the following command to download AppSignal's library files into your project
```
npx @appsignal/cli install
```
![Picture3-](https://user-images.githubusercontent.com/13951043/162178445-75ce159b-40e0-4ec3-8528-39b0407ce3e9.png)
- As a result, the installation of AppSignal will commence. The terminal will ask you about **which integration do you need**?.
  - Just press _Enter_ here, and NodeJS will be selected automatically.
  
  ![Picture4-](https://user-images.githubusercontent.com/13951043/162179024-c2afcf1d-8705-4594-9d0d-0056750e55f5.png)
  - After selecting NodeJS, you'll asked for your _Push Key_. Copy your _Push Key_ from the **Install AppSignal** page and paste it onto your terminal window.
  
  ![Picture5-](https://user-images.githubusercontent.com/13951043/162180505-ed404c5e-f68f-4188-b5d3-82b105f5b7c4.png)
  - After passing the correct _Push Key_, the installer will ask the name of your app. Type the name of your project and hit _Enter_.
  
  ![Picture6-](https://user-images.githubusercontent.com/13951043/162181379-bf1396a0-8add-408c-817b-d63bfdd03ee0.png)

  - Now the installer will look for any integrations supported by AppSignal. If found, the installer will ask you whether you would like to install those integrations or not? If no supported integration is available, you will asked to install the code of AppSignal in your NodeJS application.
  
   ![Picture7-](https://user-images.githubusercontent.com/13951043/162181864-af0beed1-95c3-425d-a837-894fc78bdce7.png)
  - Type _Y/y_ and hit _Enter_. The installation will proceed and all the necassary files will be setup automatically. Once the installation is complete, you will see a message suggesting that AppSignal has been installed successfully.
  
  ![Picture8](https://user-images.githubusercontent.com/13951043/162182540-6454f016-7aa8-4546-ae7f-d6d88ef2b6b1.png)

### Executing your application
Its time to execute your project but, before we do that we must refer to our AppSignal library inside the code so that AppSignal could recieve data generated by our application.
  - Copy the following code and paste it on top of your index.js/app.js file.
  ```
  const { Appsignal } = require("@appsignal/nodejs");

  const appsignal = new Appsignal({
    active: true,
    name: "<YOUR APPLICATION NAME>",
    pushApiKey: "<YOUR API KEY>" // Note: renamed from `apiKey` in version 2.2.5
  });

  // ...all the rest of your code goes here!
  ```
  - Replace "<YOUR APPLICATION NAME>" with your app's name used during installation.
  - Also, replace "<YOUR API KEY>" with your own _Push Key_.
  - Save all the changes; we are ready to execute our project now.
  - Since my key project file is called _index.js_, I'll type `node index` in the terminal and hit _Enter_ to execute my project. As a result, the program will start to fetch data from the blockchain as shown below.
  
  ![Picture9](https://user-images.githubusercontent.com/13951043/162185104-3cfc2ea6-0d4b-4de7-b29d-7d6042cbb478.png)

### Checking out AppSignal’s dashboard
  - While my project is up and running I'll go to the **Install AppSignal** page and click on _Next Step_.
  - This will lead me towards a landing page, where I'll wait for AppSignal to recieve data from the configured application. 
  
  ![Picture10](https://user-images.githubusercontent.com/13951043/162186431-4bb50ba8-7210-40e1-8d16-00804b43078a.png)
  - Once the data is recieved, the timer will stop and you'll see the _AppSignal is Ready_ message. Click on the **Go to app**
  - Your application's dashboard will open where all the application performance metrics will be shown to you.
  
  ![Picture11](https://user-images.githubusercontent.com/13951043/162186790-eb7935df-7ee7-4f5d-9935-381f4afb4051.png)

That's it for now, feel free to check out our [documentation](https://docs.appsignal.com/).
