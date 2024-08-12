# Build 'Always-On' applications on the Autonomous Database


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

- To start the Swingbench UI, open CMD in your Windows instance and navigate to Swingbench winbin folder.

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


You may now **proceed to the next lab**.

## Acknowledgements
*Congratulations! You successfully configured the swingbench java application with Autonomous database.*

- **Author** - Tejus Subrahmanya
- **Last Updated By/Date** - Tejus Subrahmanya, Autonomous Database Product Management, August 2024

## See an issue or have feedback?  
Please submit feedback [here](https://apexapps.oracle.com/pls/apex/f?p=133:1:::::P1_FEEDBACK:1).   Select 'Autonomous DB on Dedicated Exadata' as workshop name, include Lab name and issue / feedback details. Thank you!
