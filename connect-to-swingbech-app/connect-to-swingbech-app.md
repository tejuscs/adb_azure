# Connect Autonomous Database with Swinbench

## Introduction

In this lab we will install and configure a workload generation tool called Swingbench.

Estimated Time: 10 minutes

### Objectives

As an administrator:
1. Install and configure Swingbench to simulate a transaction processing workload.


### Required Artifacts

- A pre-provisioned instance of Autonomous database and Developer Client image. Refer to the Lab 2: **Connect securely with Visual Studio code**.

## Task 1: Download and install Swingbench

- We will start with downloading and installing Swingbench in a developer client virtual machine.

- Connect to your developer client machine via RDP. Detailed instructions are provided in that Lab 2: **Connect securely with Visual Studio code**.

    *The remainder of this lab assumes you are connected to the Windows instance through RDP  and are operating from the Windows instance itself and not your local machine (except if noted).*

- Once connected, open a Microsft Edge browser and download the latest version of swingbench.

    ````
    <copy>
    https://www.dominicgiles.com/downloads/
    </copy>
    ````

- unzip swingbench.zip. It unzips contents in the swingbench folder.

    ```
    <copy>
    cd C:\Users\opc\Downloads\swingbenchlatest
    </copy>
    ```

### JDBC Drivers in Swingbench
- You would need the jdbc drivers to run swingbench. Oracle jdbc drivers may be downloaded from [JDBC Downloads](https://www.oracle.com/java/technologies/downloads/#jdk22-windows).

- Use on screen instructions to update drivers if needed, otherwise move on to transfer DB wallet.

### Transfer DB Wallet to swingbench client machine
Unless you have already moved the wallet to your Dev Client machine in an earlier lab, follow the steps in Lab 2: **Connect securely with Visual Studio code**.


## Task 2: Connect swingbench application to Autonomous database

Now that you have installed swingbench, the next step is to connet the application to your Autonomous database.

- You are ready to run Swingbench workloads on Autonomous database. Workloads are simulated by users submitting transactions to the database.

- Load sample data to your Autonomous Database. To start oewizard to load Schema and data, navigate to Swinbench winbin folder and run oewizard.bat.

    ```
    cd C:\Users\opc\Downloads\swingbenchlatest\swingbench\winbin
    ```
    ```
    oewizard.bat
    ```

    ![This image shows the result of performing the above step.](./images/oewizard.png " ")

- Click Next and select Version 2.0.

    ![This image shows the result of performing the above step.](./images/oewizard1.png " ")

- Select Create the Order Entry Schema and click Next.

    ![This image shows the result of performing the above step.](./images/oewizard2.png " ")

- Copy the Connect string from Azure portal, and change the Username to ***Admin*** and enter your Admin password and click Next. 

    ![This image shows the result of performing the above step.](./images/connectstring.png " ")

    ![This image shows the result of performing the above step.](./images/oewizard3.png " ")

- Change the password to ***WElcome_123#*** and keep the remaing default and click Next.

    ![This image shows the result of performing the above step.](./images/oewizard4.png " ")

- Keep Database Options as default and click Next. 

    ![This image shows the result of performing the above step.](./images/oewizard5.png " ")

- Change User defined scale to ***0.1 GB*** and click Next and Finish. 

    ![This image shows the result of performing the above step.](./images/oewizard6.png " ")

- Building the simple order entry schema should be done in a few mins. 

    ![This image shows the result of performing the above step.](./images/oewizard7.png " ")

    ![This image shows the result of performing the above step.](./images/oewizard8.png " ")


- Once the Schema is created, start the Swingbench UI. Open CMD in your Windows instance and navigate to Swingbench winbin folder.

    ```
    <copy>
    cd C:\Users\opc\Downloads\swingbenchlatest\swingbench\winbin
    </copy>
    ```

    ![This image shows the result of performing the above step.](./images/cmd.png " ")

- Start Swingbench UI
    ```
    <copy>
    swingbench.bat
    </copy>
    ```
    
    ![This image shows the result of performing the above step.](./images/swingbench.png " ")

- Running the above command should open up the Swingbench configuration tool and select the following to connect Swingbench to Autonomous database. 

- Select ***SOE_Server_Side_V2*** and click OK.

    ![This image shows the result of performing the above step.](./images/swingbench1.png " ")

- Enter ***Username*** as ***soe***, ***Password*** as ***WElcome_123#*** and Connect String can be copied from the Azure portal. 

    ![This image shows the result of performing the above step.](./images/swingbench2.png " ")

    ![This image shows the result of performing the above step.](./images/connectstring.png " ")

 - Test the connectiong to the database by clicking on connect link in Connect String. If the entered details are correct, you should see a confirmation popup - ***Connected to database using supplied parameters***

    ![This image shows the result of performing the above step.](./images/connect.png " ")

- Start Benchmark run by clicking on the ***Green Play*** button

    ![This image shows the result of performing the above step.](./images/start.png " ")

- You should now see the Transaction happening in your Autonomous database. 

    ![This image shows the result of performing the above step.](./images/start1.png " ")

***NOTE: Do not disconnect the swingbench application. The next steps shows the Auto scaling capability of Autonomous Database.***

## Task 3: Enable Compute Auto Scaling in you Autonomous database

- Login to Azure portal and navigate to your Autonomous database overview page and expand ***Settings*** and click on ***Resource allocation*** and ***Manage***.

    ![This image shows the result of performing the above step.](./images/auto.png " ")

- Check on ***Compute auto scaling*** and click Apply.

    ![This image shows the result of performing the above step.](./images/auto1.png " ")

- Open Swingbench application and notice how your Transactions per minute is increasing on enabling Auto scaling. 

    ![This image shows the result of performing the above step.](./images/auto2.png " ")

- Navigate back to Azure portal and turn off Auto Scaling. 

You may now **proceed to the next lab**.

## Acknowledgements
*Congratulations! You successfully configured the swingbench java application with Autonomous database and observed how compute auto scaling can benfit your applications .*

- **Author** - Tejus Subrahmanya
- **Last Updated By/Date** - Tejus Subrahmanya, Autonomous Database Product Management, August 2024

## See an issue or have feedback?  
Please submit feedback [here](https://apexapps.oracle.com/pls/apex/f?p=133:1:::::P1_FEEDBACK:1).   Select 'Autonomous DB on Dedicated Exadata' as workshop name, include Lab name and issue / feedback details. Thank you!
