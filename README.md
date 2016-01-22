#Desk.com with Nexmo SMS

<img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image1.png" width=200>

##Introduction

Salesforce Desk.com offers small businesses an all-in-one customer service software solution that will help keep their customers happy and loyal. Desk.com can be set up in just few hours, and provides multi-channel support, including phone, email, self-help pages and social media. This innovative help desk software will let the agents more easily serve end customers, have the insights needed to build better products and make smarter, growth-driven decisions.

Integration of Desk.com with Nexmo SMS will allow Desk.com users to send SMS to the requester on various stages/events of his/her cases on Desk.com. User can configure the event as well as the respective SMS text.

##Use case

User can send SMS to the requester over various events - whenever a new case is created, opened, reopened, updated or pending.

##Prerequisites 

-   Desk.com environment with admin credentials.

-   Nexmo subscription and corresponding Nexmo API keys (Keys and Secret). To access the API keys, see the appendix section.

-   Internet connectivity.

##Features 

-   Send SMS on the selected events

-   Allows user to add custom text for SMS

-   Custom placeholder (Liquids) or fields in SMS

##Steps to configure Desk.com with Nexmo SMS 

1.  Log in on Desk.com with admin credentials.

2.  You will land on the following dashboard.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image3.png" width=600>

    If your interface is different than click on **Classic Agent** drop down from the left top bar and select **Next Gen Agent** as shown.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image4.png" width=600>

3.  Click on **Admin** from the left panel.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image5.png" width=600>

4.  You will land on following screen click on **APPS**

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image6.png" width=600>

5.  You will see a list of apps. Search for **Custom Action** app and click on **Install**.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image7.png" width=600>

6.  On the next screen, click on **Install** **Custom Action**.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image8.png" width=600>

7.  Scroll down to accept the agreement.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image9.png" width=600>

8.  Give your app instance a Name, Authentication method, and URL. We have chosen **None** for authentication and put desk.com url in URL field. Make sure it is activated. Click on create.

	<img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image10.png" width=600>

9.  After installation, you will see the following screen; click on **Add Action**.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image11.png" width=600>

10. You will get a **CREATE A NEW ACTION** pop up as shown.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image12.png" width=600>

11.  Give your action a name and in **Action Type** dropdown, select **POST a JSON string to a URL**.

    In **Append URL path** field, put Nexmo SMS API URL (<http://rest.nexmo.com/sms/json>?) and for **JSON to POST** field, put the following JSON object.

    Replace credentials and settings as per your need. In this example, we are creating an action to send SMS on case creation.

    {

    "api\_key":"YOUR\_API\_KEY",

    "api\_secret":"YOUR\_API\_SECRET",

    "to":"{{case.customer.phone}}",

    "from":"YOUR\_FROM\_NUMBER",

    "text":"The ticket ID {{case.id}} is created."

    }

    Final settings will look like as shown below:

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image13.png" width=600>

12.  By using liquid variables you can make the SMS dynamic. For a list of liquid variables, please refer (<https://support.desk.com/customer/portal/articles/2916-list-of-liquid-variables>)

13.  Click on **Add Action** button at the bottom.

14.  Click on the grey button to activate it.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image14.png" width=600>

15.  We need to create a rule for the action we defined in previous steps. Click on **CASES** from the top menu and then on **Rules** from the side menu.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image15.png" width=600>

16.  Click on **Case Created** from the side menu and then click on **Add Rule**.

    **Note: You can choose any other event like Case Opened, Case Reopened, Case uploaded** etc., as per your need.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image16.png" width=600>

17.  In the pop up, give your rule a name and click on **Add**.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image17.png" width=600>

18. In next pop up, in **Rule Actions,** select **Trigger an App Action** in the first drop down and **Custom action : &lt;YOUR APP INSTANCE NAME &gt;** in the second drop down. You can change other settings as per need.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image18.png" width=600>

19. Your rule is created. Click on the grey button to activate it if it is not already.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image19.png" width=600>

    You are done. Now you should receive an SMS when a case is created.

##Creating a case

1.  Click on **Admin -&gt; Next Gen Agent**.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image20.png" width=600>

2.  Click on the following button on the top bar.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image21.png" width=600>

3.  For example - If we are creating a case for a phone call, the **Phone** icon is already selected so you can search or create a new customer here. If the number is already saved, it will show you a suggestion, else you can click on the **Add new customer**.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image22.png" width=600>

4.  It will ask you for the details of the new customer.

    <img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image23.png" width=600>

    Fill in these details and click on **Create.**

5.  You will get an SMS for the newly created case.

##Appendix

Nexmo API Keys
------------------------------------------------------------------------------------------------------------

-   To access the Nexmo keys, go to <https://www.nexmo.com/> and sign-in.

-   On the top right corner, click on the **Api Settings**.

-   Key and Secret will display in the top bar as shown in the below image:

	<img src="https://github.com/AdvaiyaLabs/Desk.com-with-Nexmo-SMS/blob/master/Docs/image24.png" width=600>
