# IBM API Connect

## Create and Secure an API to Proxy an Existing REST Web Service

[Return to main APIC lab page](../ReadMe.md#lab-abstracts)

---

# Table of Contents
- [1. Introduction](#introduction)

- [2. Import an API into the Developer Workspace](#import_api)

- [3. Configure the API ](#configure_api)
	* [3a. Configure Client Secret API Key Security](#configure_security)
	* [3b. Review and update the Target-URL for Sandbox Environment](#target_url)
	* [3c. Review the Proxy Call in Designer](#proxy)

- [4. Test the API](#test_api)

- [5. Publish API](#publish_api)
	* [5a. Create Customer Product and Add API](#customer_product)

- [6. Summary](#summary)

---

# 1. Introduction <a name="introduction"></a>

In this lab, we will get a chance to use the IBM API Connect (APIC) Designer and its intuitive interface to import and edit an API using the OpenAPI definition (YAML) of an existing Customer Database RESTful web service.

In this tutorial, we will explore the following key capabilities:

-   Creating an API by importing an OpenAPI definition for an existing REST service

-   Configuring ClientID/Secret Security, endpoints, and proxy to invoke an endpoint

-   Testing a REST API in the developer toolkit

-   Publish an API for developers

# 2. Import an API into the Developer Workspace <a name="import_api"></a>

If you're not logged before, follow these instructions to access to the API Manager ->
[Login to the API Manager](../Login-apic/ReadMe.md)

1\. Confirm that you are in the provider organization for your username (upper right) and then click on **Develop APIs and products**.

![alt text][pic9]

2\. We are now able to begin to create APIs and Products.  Click **Add**.

![alt text][pic10]

3\. Click **API (from REST, GraphQL or SOAP)**.

![alt text][pic11]

4\. Click **From existing OpenAPI service** under **Create** and click **Next**.

![alt text][pic12]

5\. [Download the **Customer_Database-1.0.0.yaml** file for an existing REST service.](./resources/Customer_Database-1.0.0.yaml)

6\. Drag and drop the yaml file that you just downloaded or click to upload. Once you have dragged and dropped or uploaded, you will see the yaml file listed under and should see a notification that the "YAML has been successfully validated". Click **Next**.

![alt text][pic13]

7\. Review the basic info for the API and click **Next**. 

![alt text][pic105]

8\. Make sure that the **Activate API** <span style="color: red">is not</span> selected and click **Next**. 

![alt text][pic14]

9\.  The API should be imported successfully as shown in the image below.  Click **Edit API**.

![alt text][pic15]

[pic0]: images/0.png
[pic1]: images/1.png
[pic2]: images/2.png
[pic3]: images/3.png
[pic4]: images/4.png
[pic5]: images/5.png
[pic91]: images/91.png
[pic92]: images/92.png
[pic93]: images/93.png
[pic94]: images/94.png
[pic95]: images/95.png
[pic96]: images/96.png
[pic97]: images/97.png
[pic98]: images/98.png
[pic99]: images/99.png
[pic100]: images/100.png
[pic101]: images/101.png
[pic102]: images/102.png
[pic103]: images/103.png    
[pic6]: images/6.png
[pic7]: images/7.png
[pic8]: images/8.png
[pic9]: images/9.png
[pic10]: images/10.png
[pic11]: images/11.png
[pic12]: images/12.png
[pic13]: images/13.png
[pic14]: images/14.png
[pic15]: images/15.png
[pic104]: images/104.png
[pic105]: images/105.png

# 3. Configure the API <a name="configure_api"></a>

After importing the existing API, it is already configured with basic Client Id API Key security for consumer identification. Now we are going to add extra security before exposing it to other developers so that we are able to authenticate the application using the API.

Next, we will review the backend endpoints where the API is actually running. IBM API Connect supports pointing to multiple backend endpoints to match your multiple build stage environments.

Finally, we will review the proxy call to invoke the endpoint.

## 3a. Configure Client Secret API Key Security <a name="configure_security"></a>

1\. Make sure that the **Design** tab is selected and click on the (**+**) next to **Security Schemes**.

![alt text][pic31]

12\. For the **Security Definition Name (Key)**, enter a name (e.g., **ClientSecret**) and select **apiKey** in the drop-down menu for **Security Definition Type**.

![alt text][pic32]

13\. Select **client_secret** from the drop-down menu for **Key Type (optional)**, and select **header** from the drop-down menu for **Located In**. For the **Variable Name**, enter a name (e.g., **X-IBM-Client-Secret**). Click **Create**.

![alt text][pic33]

14\. Click **Save**.

![alt text][pic26]

15\. Once saved, you will see an indicator window appear that shows that **Your API has been updated**.  Click on the [**x**] to close the window.

![alt text][pic22]

16\. Make sure that the **Design** tab is selected. Click on the **Security** section and then click on the **pencil** icon to edit the existing security configuration

![alt text][pic34]

17\. Select both **"clientID"** and **"clientSecret"** and click **Submit**.

![alt text][pic37]

18\. Click **Save**.

![alt text][pic26]

19\. Once saved, you will see an indicator window appear that shows that **Your API has been updated**.  Click on the [**x**] to close the window.

![alt text][pic22]

## 3b. Review and update the Target-URL for Sandbox Environment <a name="target_url"></a>

1\. Navigate to the **Gateway** tab.

![alt text][pic40]

2\. Make sure that the **Gateway** tab is selected and expand **Properties**.  Click on **target-url**.

![alt text][pic41]

3\. Review  the **Property Value (optional)** and replace the cluster name (e.g.**wedge**) with the value that applies to your actual cluster.

![alt text][pic42]

4\. Click **Save**.

![alt text][pic26]

5\. Once saved, you will see an indicator window appear that shows that **Your API has been updated**.  Click on the [**x**] to close the window.

![alt text][pic22]

## 3c. Review the Proxy Call in Designer <a name="proxy"></a>

1\. Navigate to the **Gateway** tab.

![alt text][pic48]

2\. Make sure the **Gateway** tab is selected and click on **Policies**.

![alt text][pic49]

3\. Click on the **Invoke** task in the assembly panel.

![alt text][pic50]

4\. Review the **URL** and update if needed so that it reads `$(target-url)$(request.path)`.

![alt text][pic51]

5\. Click **Save**.

![alt text][pic52]

6\. Once saved, you will see an indicator window appear that shows that **Your API has been updated**.  Click on the [**x**] to close the window.

![alt text][pic53]

[pic16]: images/16.png
[pic17]: images/17.png
[pic18]: images/18.png
[pic19]: images/19.png
[pic20]: images/20.png
[pic21]: images/21.png
[pic22]: images/22.png
[pic23]: images/23.png
[pic24]: images/24.png
[pic25]: images/25.png
[pic26]: images/26.png
[pic27]: images/27.png
[pic28]: images/28.png
[pic29]: images/29.png
[pic30]: images/30.png
[pic31]: images/31.png
[pic32]: images/32a.png
[pic33]: images/33.png
[pic34]: images/34.png
[pic35]: images/35.png
[pic36]: images/36.png
[pic37]: images/37.png
[pic38]: images/38.png
[pic39]: images/39.png
[pic40]: images/40.png
[pic41]: images/41.png
[pic42]: images/42.png
[pic43]: images/43.png
[pic44]: images/44.png
[pic45]: images/45.png
[pic46]: images/46.png
[pic47]: images/47.png
[pic48]: images/48.png
[pic49]: images/49.png
[pic50]: images/50.png
[pic51]: images/51.png
[pic52]: images/52.png
[pic53]: images/53.png

# 4. Test the API <a name="test_api"></a>

In the API Designer, you have the ability to test the API immediately after creation in the Assemble view!

1\. Switch the toggle from Offline to Online. This step automatically publishes the API.

![alt text][pic54]

2\. You will see an indicator window appear that shows that **Your API has been updated**.  Click on the [**x**] to close the window.  You should see that the API is now Online.

![alt text][pic55]

3\. Click on the **Test** tab.

![alt text][pic56]

4\. For the **Request**, select the request that begins with **GET** and ends in `../customerdb/v1/customers`.  Click **Send**.

![alt text][pic57]

**Note:** If this is the first time testing the API after publishing it, you may get a **No response received** popup. Click **Here** and accept the certificate to see the 401 message.

![alt text][pic58]

To add an exception in the Chrome browser, click in the whitespace of the page.

![alt text][pic59]

Blindly type `thisisunsafe`.  This should direct you to a new page that states **401 - Unauthorized**.

![alt text][pic60]

Navigate back to the **API Connect** browser window.

To add an exception in the Firefox browser, click **Advanced** and click **Accept the Risk and Continue**.

![alt text][pic61]

![alt text][pic62]

This will direct you to a new page that states **401 - Unauthorized**.

![alt text][pic63]

Navigate back to the **API Connect** browser window.

5\. Click **Send**.

![alt text][pic57]

6\. The **Response** will show all of the customers in the database.

![alt text][pic64]

7\. Now let's add a record to the database.  Click **Clear**.

![alt text][pic65]

8\. For the **Request**, select the request that begins with **POST** and ends in `../customerdb/v1/customers`.  Click on the **Body** tab.

 ![alt text][pic66]

9\. In the **Body** tab, enter some text in the following JSON format:
```
{
"firstname" : "Emily",
"lastname" : "Drew",
"address" : "123 Colorado Address"
}
```

Click **Send**.

![alt text][pic67]

10\. Make note of the **ID** number in the response.  In the example below, the ID is 9.

![alt text][pic68]

11\. For the **Request**, select the request that begins with **GET** and ends in `../customerdb/v1/customers/{customerId}` and click **Clear**.

![alt text][pic69]

12\. Click on the **Parameters** tab and enter the **ID** that you noted in step 10. Click **Send**.

![alt text][pic70]

13\. In the response, you will see the customer information that you entered in step 9.

![alt text][pic71]

14\. We can now update the customer information. For the **Request**, select the request that begins with **PUT** and ends in `../customerdb/v1/customers/{customerId}` and click **Clear**.

![alt text][pic72]

15\. Enter the **ID** that you noted in step 10 and click on the **Body** tab.

![alt text][pic73]

16\. In the **Body** tab, enter some text in the following JSON format:
```
{
  "firstname": "Emily",
  "lastname": "Drew",
  "address": "123 Colorado Address"
}
```
and click **Send**.

![alt text][pic74]

17\. The response should show that the customer ID was updated.

![alt text][pic75]

18\. For the **Request**, select the request that begins with **GET** and ends in `../customerdb/v1/customers/{customerId}` and click **Clear**.

![alt text][pic69]

19\. Make sure that the **Parameters** tab is selected and enter the **ID** that you noted in step 10. Click **Send**.

![alt text][pic70]

20\. In the response, you will see the customer information that you entered in step 16.

![alt text][pic76]

21\. You can also delete a customer from the customer database.  For the **Request**, select the request that begins with **DELETE** and ends in `../customerdb/v1/customers/{customerId}` and click **Clear**.

![alt text][pic77]

22\. Make sure that the **Parameters** tab is selected and enter the **ID** that you noted in step 10 and enter `secr3t` for **Authorization**. Click **Send**.

![alt text][pic78]

23\. In the response, you will see the customer was deleted.

![alt text][pic79]

[pic54]: images/54.png
[pic55]: images/55.png
[pic56]: images/56.png
[pic57]: images/57.png
[pic58]: images/58.png
[pic59]: images/59.png
[pic60]: images/60.png
[pic61]: images/61.png
[pic62]: images/62.png
[pic63]: images/63.png
[pic64]: images/64.png
[pic65]: images/65.png
[pic66]: images/66.png
[pic67]: images/67.png
[pic68]: images/68.png
[pic69]: images/69.png
[pic70]: images/70.png
[pic71]: images/71.png
[pic72]: images/72.png
[pic73]: images/73.png
[pic74]: images/74.png
[pic75]: images/75.png
[pic76]: images/76.png
[pic77]: images/77.png
[pic78]: images/78.png
[pic79]: images/79.png

# 5. Publish API <a name="publish_api"></a>

In this lab, we will make the API available to developers. In order to do so, the API must be first put into a product and then published to the Sandbox catalog. A product dictates rate limits and API throttling.

When the product is published, the Invoke policy defined in the previous lab is written to the gateway. 

## 5a. Create Customer Product and Add API <a name="customer_product"></a>

1\. From the vertical navigation menu on the left, click **Develop**.

![alt text][pic80]

2\. Click the **Products** tab.

![alt text][pic82]

3\. Click **Add** and click **Product** from the drop-down menu.

![alt text][pic83]

![alt text][pic84]

4\. Click **New product** and click **Next**.

![alt text][pic85]

5\. Enter **Customer** for the **Title** and click **Next**.

![alt text][pic86]

6\. Select the **Customer Database** API and click **Next**.

![alt text][pic87]

7\. Keep the **Default Plan** as is and click **Next**.

![alt text][pic88]

8\. Select **Publish product** and confirm that **Visibility** is set to **Public** and **Subscribability** is set to **Authenticated**.  Click **Next**.

![alt text][pic89]

9\.  The Product is now published successfully with the API base URL listed and available for developers from the Developer Portal.  Click **Done**.

![alt text][pic90]

[pic80]: images/80.png
[pic81]: images/81.png
[pic82]: images/82.png
[pic83]: images/83.png
[pic84]: images/84.png
[pic85]: images/85.png
[pic86]: images/86.png
[pic87]: images/87.png
[pic88]: images/88.png
[pic89]: images/89.png
[pic90]: images/90.png

# 6.Summary <a name="summary"></a>

Congratulations, you have completed the **Create and Secure an API** lab. Throughout the lab, you learned how to:

-   Create an API by importing an OpenAPI definition for an existing REST service

-   Configure ClientID/Secret Security, endpoints, and proxy to invoke endpoint

-   Test a REST API in the Developer Toolkit

-   Publish an API for developers

[Return to main APIC lab page](../ReadMe.md#lab-abstracts)
