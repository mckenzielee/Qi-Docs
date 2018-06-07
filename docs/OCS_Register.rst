Register client applications with OSIsoft Cloud Services 
========================================================

Overview 
--------

Authentication for OSIsoft Cloud Services (OCS) is managed by obtaining tokens from your Azure Active Directory 
(Azure AD). These tokens are authorized either by a signed-in user or by a client application’s 
credentials/identity. To integrate and authenticate client applications with OCS, registering an Azure AD 
application enables application credentials to be generated. Because OCS has read-only access to your 
Azure AD, you must use the Azure Portal to register an application before you can authenticate with OCS. 

You must have appropriate permissions within Azure AD to create and register an application. After the 
application has been registered with Azure AD, it must also be registered with OCS. Only users with OCS 
Account Administrator role can register applications with OCS. The following sections describe how to 
register applications in both Azure AD and OCS. 

Register an application in Azure Active Directory 
-------------------------------------------------

1. Log in to the Azure Portal.  
   Ensure you are logged into the correct directory by verifying the directory name in the menu bar at the 
   top of the page. You must have permissions to create applications in Azure. 

2. Click **More Services** and choose **Azure Active Directory**. 

3. Click the **App Registrations** pane and select **New application registration**. 
   
4. In the **Name** field, enter a name for your application.  

5. Select **Web app / API** as the Application type.  

6. In the **Sign-on URL** field, enter a URL that uniquely identifies the application within your company’s Azure Active Directory. 

7. After the application displays in the list, select it and then click **Settings**. 

8. Navigate to the **Required Permissions** section, select the default **Windows Azure Active Directory** permissions, 
   and click the delete icon. 

9. Select **Add** to add API access. 

10. In the **Select an API** pane, search for and select **OSIsoft Cloud Services** and click **Select**.  
    The Select Permissions pane displays after you select OSIsoft Cloud Services. 

11. From the **Select permissions** pane, select the OSIsoft Cloud Services API application permissions checkbox. 
    Click **Select** and then click **Done** to add the permissions to the application. 

12. Click on **Grant Permissions** for the permissions change to take effect. 

13. Navigate to the **Keys** pane and add a new Client Key with the appropriate description and expiration duration.  
    The key is displayed after clicking the Save button. After the pane is closed, the key is no longer visible. 
    Store the key in a secure location, such as in an Azure Key Vault. Use the Application ID and the key as shown 
    in the code samples on the OSIsoft Cloud Services **Client Keys** page. 
 

Register an application in OSIsoft Cloud Services 
-------------------------------------------------

1. Navigate to the OSIsoft Cloud Services portal and log in to your account using your credentials. 
   You must have the account administrator role to register applications with OSIsoft Cloud Services. 

2. Navigate to the **Client Keys** page in the left-hand navigation pane. 

3. Click the **Add** 

.. image:: images/Add_Button.png button.  


4. Specify a search query and select **Search** to find the application from the directory in the popup window.  
   The search query can be the name of either the application or the application ID, which is a GUID. 

5. Select the application and the appropriate roles for the application.  

6. Click **Add**.  
 

The application is now registered with OSIsoft Cloud Services. You are now able to connect applications 
to OSIsoft Cloud Services and send and receive data. 

 

 
