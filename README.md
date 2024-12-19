<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


osTicket is an open-source help desk ticketing system used to keep track of issues and the resolutions to those issues as they relate to products or services. 



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
   https://portal.azure.com/
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

1) Create a virtual machine in Microsoft Azure with the specs of Windows 10 Pro, version 22H2 with at least 2vcpus and 16 gbs of memory. Name the virtual machine osTicket-vm. 

2) Sign in to the virtual machine using Remote Desktop Connection with the public IP address.

   ![IP Address](https://github.com/user-attachments/assets/a1c74e9b-cc5f-4b07-938b-b87bfe8443bf)


![RDP](https://github.com/user-attachments/assets/d125b089-25b5-4682-af3b-513ea15bbe6c)

The username and password are the ones we created in Azure.



![VM Password](https://github.com/user-attachments/assets/fd79bfb7-2589-42cd-a7c3-9da1b0cba0e4)



   *****From here on all the work will be done within our virtual machine. Do not perform these actions on your actual computer.****


 3) Search for Control Panel in the windows bar and select Programs Then select Windows feature on and off. From there we will enable IIS Windows with CGI.

   ![Control Panel](https://github.com/user-attachments/assets/ac474e99-494e-49ab-8a16-c5fa1291f935)


![Windows on off](https://github.com/user-attachments/assets/4b78cc44-bb69-463b-a0dd-8e9895a2992e)


  Pathway: IIS -> World Wide Web Services -> Application Development Features -> CGI


![CGI](https://github.com/user-attachments/assets/ea139b48-2263-47dd-9ef1-105a4a34db8e)




4) Browse to 127.0.0.1 This will eventually become the osTicket installer.

   ![127 0 0 1](https://github.com/user-attachments/assets/df67b00c-41f2-429f-a034-6579d7601e1c)



5) Download and install PHP Manager and Rewrite Module from the google drive.

   ![instilllation](https://github.com/user-attachments/assets/1b3cf224-06e0-466e-8b77-55a18649564b)





   

6) In the Windows C Drive create a new folder named PHP

![PHP](https://github.com/user-attachments/assets/d47783fa-7cdd-4d1c-95bc-d349ad431bcf)


7)  Download PHP 7.3.8 then right-click the download and extract all into new PHP folder created in the C Drive.



   ![Extraxt PHP](https://github.com/user-attachments/assets/a78832c6-4252-47d9-8659-f07fb7c6f43f)

8) Download and install VC_redist.x86.exe

9) Download and install MySQL 5.5.62

   When installing this program be sure to select "Typical"  and "Standard Configuration". We will use "root" as our password. Then execute.

   ![Typical](https://github.com/user-attachments/assets/8fb48bdb-cf66-4792-9c42-135b8cad2289)

![Standard](https://github.com/user-attachments/assets/99fbadb5-05e9-407d-9ec4-ce25c6cc2c59)


  ![root](https://github.com/user-attachments/assets/41dd0085-29ea-4f13-8827-3141d739a826)


10) Search for IIS in the windows bar and run it as an adminitrator by right clicking it. The IIS Manager will open. 
 
![IIS admin](https://github.com/user-attachments/assets/52f72207-0b13-4805-81b6-4ec40717f247)

Double-click PHP Manager.

![IIS Home](https://github.com/user-attachments/assets/b5830ace-0a03-4883-9abc-67d39a5dc144)


 Click on Register new PHP version.

![Register new](https://github.com/user-attachments/assets/782f1af7-7597-4ac6-8b61-bc9f5f08fd39)


Click the 3 dots.

![3dots](https://github.com/user-attachments/assets/a5ea2a78-f091-4c83-9ba5-9f4e992d3335)







Go to C Drive -> PHP -> click on php-cgi file.

It should now look like this.

![execute php](https://github.com/user-attachments/assets/6e198d57-d854-46d0-a771-01de518f7431)



11) Stop and Start the server.

![STOpStart](https://github.com/user-attachments/assets/a318350f-9c27-4fd1-a818-488013137d45)


12) Download and install osTicket v1.15.8.

Extract files from the download to the "root" file.


    Pathway: C Drive -> inetpub -> root

  
![wwwroot](https://github.com/user-attachments/assets/9e750d0e-8988-42f3-8cb6-f8cc86c45b4f)

  
    Witin wwwroot rename "upload" file.

![upload](https://github.com/user-attachments/assets/b4ad8897-bf0f-4e81-9253-cbce62e15e6b)

to "osTicket"

  ![osTicket](https://github.com/user-attachments/assets/25c6528b-ea9f-4713-9dce-3d837038e349)

13) Stop and Start server, again.

    Follow this path: osTicket-vm -> Sites -> osTicket

    Then click on browse *:80 

![browse 80](https://github.com/user-attachments/assets/287f005e-491a-48f1-b1ac-7e5b13834add)

The 127.0.01 should now refresh to a new page.

You will notice that some of the extensions are not enabled.

![os installer](https://github.com/user-attachments/assets/4dd7f95d-3ec4-4918-8692-45c137b6935b)


14) Enable the extensions in the IIS Manager. Double-click on PHP Manager.

    
Click Enable or disable an extension.

![enable](https://github.com/user-attachments/assets/2947c32c-e262-4acb-a8c6-930d082e3b8d)

Here, we will enable three extensions.

php-intl.dll

php_opcache.dll

php_imap.dll

![php extentions](https://github.com/user-attachments/assets/a8bd2032-429a-47e5-9c98-e30bc065773e)

The website should now look like this.

![New osTicket website](https://github.com/user-attachments/assets/f7dbb362-e5fa-4b6f-acea-5fa66ec63a6b)



15) Rename ost-sampleconfig.php

    Pathway: C Drive -> inetpub -> wwwroot -> osTicket -> include -> ost-sampleconfig.php

   ![sampleconfig](https://github.com/user-attachments/assets/9be46931-a9a6-4ba9-a93f-4324ac5e34e6)


   New name.
   
![ost rename](https://github.com/user-attachments/assets/8d2170d2-c8fc-4d1d-af16-fbcc9acd3082)

   
 16) Now we will add new permissions.
 
 Right-click on ost-config.php file. Go to properties.

 ![properties](https://github.com/user-attachments/assets/783766a3-b802-4315-9186-d5cd92eefce4)


Click Security then Advanced.

![security](https://github.com/user-attachments/assets/0857fd7a-3b13-4795-96e5-ca423b066b72)


Disable the inheritance.

![disable](https://github.com/user-attachments/assets/b5ac97a8-f0a8-489f-acb1-63e7ed382ed0)


Select Remove all inherited permissions from this object.

![remove](https://github.com/user-attachments/assets/e6dd2a47-2174-4526-af0e-b736e097c76b)

Click Add.

![add](https://github.com/user-attachments/assets/c5cd0a5a-d2ac-4864-bf6d-6af2b2437d1e)



Select principal.

![principal](https://github.com/user-attachments/assets/372a2de6-d969-4378-9080-4ae8d107ccb8)




Type "Everyone" in the open field.

![everyone](https://github.com/user-attachments/assets/3d592c38-c772-422c-9227-d50e0922ffb0)


Check Full Control the click and Okay.

![Full](https://github.com/user-attachments/assets/4358bdc4-1a40-4dfe-ac53-d2aae814688d)

Click Apply and then Okay.

![apply](https://github.com/user-attachments/assets/6a05e5e5-b236-4095-93a8-81a7b0053081)

17) Now return to the osTicket installer webpage and click continue.

    Fill out the information required as it pertains to you.

    ![os info](https://github.com/user-attachments/assets/8591e1a4-ee66-40fd-b627-eafd9f44e9b4)

18) Download and install HeidiSQL.

      Click next til you get to Finish. Skip the Donate page. Program should open. 

19) Now we will create a new session.

    Click New and use the "root" password we created then click Open.

    ![new](https://github.com/user-attachments/assets/7a1fa369-70eb-48cc-8c74-55e5b7110572)

20)  Let's fill in the info for Database Settings.

    Username and Password: root.

    

    MySQL Database: osTicket


 
    Within HeidiSQL, right-click on Unnamed then create new then database. Type the name "osTicket".

![unnamed](https://github.com/user-attachments/assets/3b2ca36e-9f2d-4ecb-a1b0-55664732c8a0)




    Back within the osTicket browser, type "osTicket" in MySQL Database field. Click Install Now.

![install](https://github.com/user-attachments/assets/aa3d7a85-93c8-4395-ad5b-e022e21dcfff)

    The page should automatically refresh:

   ![congratulations](https://github.com/user-attachments/assets/9cff80da-3e7f-464e-b7c8-6b416133109a)



Now we can browse to the Help Desk login page and the End user osTicket page.

Help Desk login page. 
http://localhost/osTicket/scp/login.php

![help desk](https://github.com/user-attachments/assets/3b177e05-589c-4e9d-a005-e5f8f2d65bbf)



End User osTicket page.
http://localhost/osTicket/


![image](https://github.com/user-attachments/assets/fcd804e6-da88-4518-a647-112ec9d43c0e)


Congrats! We have completed the osTicket instillation!
