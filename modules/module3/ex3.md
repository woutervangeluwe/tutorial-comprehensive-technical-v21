---
title: Foundation - Real-time Customer Profile - Visualize your own real-time customer profile - API
description: Foundation - Real-time Customer Profile - Visualize your own real-time customer profile - API
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 818e4dda-5e56-4444-9ecf-a7cc6776e693
---
# 3.3 Visualize your own real-time customer profile - API

In this exercise, you'll use Postman and Adobe I/O to query Adobe Experience Platform's APIs to view your own real-time customer profile.
 
## Story

In the Real-time Customer Profile, all profile data is shown alongside event data, as well as existing segment memberships. The data shown can come from anywhere, from Adobe applications and external solutions. This is the most powerful view in Adobe Experience Platform, the experience system of record.

The Real-time Customer Profile can be consumed by all Adobe applications, but also by external solutions like Call Centers or in-store clienteling apps. The way to do this is to connect those external solutions to Adobe Experience Platform's APIs.

## 3.3.1 - Your Identifiers

On the X-ray panel on the website, you can find multiple identities. Every Identity is linked to a Namespace. 

![Customer Profile](./images/identities.png)

On the X-ray panel, we can see 4 different combinations of IDs and Namespaces:

| Identity     | Namespace       |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID)          | 70064353701262275980354366981653865618 |
| Email ID          | woutervangeluwe+28052020-10@gmail.com|
| Mobile Number ID          | +32473622044+28052020-10|

Remember these identifiers for the next step.

With these IDs in mind, go to Postman.

## 3.3.2 - Setup your Adobe I/O Project

In this exercise you'll be using Adobe I/O quite intensively to query against Platform's APIs. Please follow the below steps to setup Adobe I/O.

Go to [https://console.adobe.io/projects](https://console.adobe.io/projects)

![Adobe I/O New Integration](./images/iohome.png)

Make sure to select the correct Adobe Experience Platform instance in the top right corner of your screen. 

![Adobe I/O New Integration](./images/iocomp.png)

Click **Create new project**.

![Adobe I/O New Integration](./images/adobe_io_new_integration.png) or 
![Adobe I/O New Integration](./images/adobe_io_new_integration1.png)

Select **+ Add to Project** and select **API**.

![Adobe I/O New Integration](./images/adobe_io_access_api.png)

You'll then see this:

![Adobe I/O New Integration](./images/api1.png)

Click the **Adobe Experience Platform** icon.

![Adobe I/O New Integration](./images/api2.png)

Click **Experience Platform API**.

![Adobe I/O New Integration](./images/api3.png)

Click **Next**.

![Adobe I/O New Integration](./images/next.png)

You can now choose to either have Adobe I/O generate your security key pair, or upload an existing one. 

Choose **Option 1 - Generate a key pair**.

![Adobe I/O New Integration](./images/api4.png)

Click **Generate keypair**.

![Adobe I/O New Integration](./images/generate.png)

You'll see a spinner for about 30 seconds.

![Adobe I/O New Integration](./images/spin.png)

You'll then see this, and your generated keypair will be downloaded as a zip file: **config.zip**.

Unzip the file **config.zip** on your desktop, you'll see it contains 2 files:

![Adobe I/O New Integration](./images/zip.png)

* **certificate_pub.crt** is your Public key certificate. From a security perspective, this is the certificate that is freely used to setup integrations with online applications.
* **private.key** is your Private key. This should never, ever be shared with anyone. The Private Key is what you use to authenticate to your API implementation and is supposed to be a secret. If you share your Private Key with anyone, they can access your implementation and abuse the API to ingest malicious data into Platform and extract all the data that sits in Platform.

![Adobe I/O New Integration](./images/config.png)

Make sure to save the **config.zip** file in a safe location, as you'll need this for the next steps and for future access to Adobe I/O and Adobe Experience Platform APIs.

Click **Next**.

![Adobe I/O New Integration](./images/next.png)

You now have to select the **Product Profile(s)** for your integration. 

Select the required Product Profiles. 

**FYI**: in your Adobe Experience Platform instance, the Product Profiles will have a different naming. You need to select at least one product profile with the proper access rights, which are set up in the Adobe Admin Console.

![Adobe I/O New Integration](./images/api9.png)

Click **Save Configured API**.

![Adobe I/O New Integration](./images/saveconfig.png)

You'll see a spinner for a couple of seconds.

![Adobe I/O New Integration](./images/api10.png)

And next, you'll see your integration.

![Adobe I/O New Integration](./images/api11.png)

Click the **Download for Postman** button and then click **Service Account (JWT)** to download a Postman environment (wait until the environment is downloaded, this can take a couple of seconds).

![Adobe I/O New Integration](./images/iopm.png)

Scroll down until you see **Service Account (JWT)**, which is where you can find all your integration details that are used to configure the integration with Adobe Experience Platform.

![Adobe I/O New Integration](./images/api12.png)

Your IO Project currently has a generic name. You need to give a friendly name to your integration. Click on **Project 1** (or similar name) as indicated

![Adobe I/O New Integration](./images/api13.png)

Click **Edit Project**.

![Adobe I/O New Integration](./images/api14.png)

Enter a Name and Description for your integration. As a naming convention, we'll use **AEP API ldap**. Replace ldap with your ldap.
For instance, if your ldap is vangeluw, the name and description of your integration becomes Platform API vangeluw.

Enter **AEP API ldap** as the **Project Title**. Click **Save**.

![Adobe I/O New Integration](./images/api15.png)

Your Adobe I/O integration is now finished.

![Adobe I/O New Integration](./images/api16.png)

## Exercise 3.3.3 - Postman authentication to Adobe I/O

Go to [https://www.getpostman.com/](https://www.getpostman.com/). 

Click on **Get Started**.

![Adobe I/O New Integration](./images/getstarted.png)

Next, download and install Postman.

![Adobe I/O New Integration](./images/downloadpostman.png)

After installation of Postman, start the application.

In Postman, there are 2 concepts: Environments and Collections.

* The Environment contains all of your environmental variables which are more or less consistent. In the Environment, you'll find things like the IMSOrg of our Platform environment, alongside security credentials like your Private Key and others. The environment file is the one you downloaded during the Adobe I/O setup in the previous exercise, it's name like this: **service.postman_environment.json**.
  
* The Collection contains a number of API requests that you can use. We will use 2 collections
  * 1 Collection for Authentication to Adobe I/0
  * 1 Collection for our Exercises

Please download **postman.zip** from the [Module 3 Prerequisites ](./real-time-customer-profile.md) to your local desktop. 

In this **postman.zip** file, you'll find the following files:

* _Adobe I-O - Token.postman_collection.json
* _Adobe Experience Platform Enablement.postman_collection.json
  
Unzip the **postman.zip** file and store these 2 files in a folder on your desktop, together with the downloaded Postman environment from Adobe I/O. You need to have these 3 files in that folder:

![Adobe I/O New Integration](./images/pmfolder.png)

Go back to the Postman UI.

![Adobe I/O New Integration](./images/postmanui.png)

In Postman, click on **Import**.

![Adobe I/O New Integration](./images/import.png)

Click on **Choose files**.

![Adobe I/O New Integration](./images/choosefiles.png)

Navigate to the folder on your desktop in which you extracted the 3 downloaded files. Select these 3 files at the same time and click **Open**.

![Adobe I/O New Integration](./images/selectfiles.png)

After having clicked **Open**, Postman will show you an overview of the Environment and Collections you're about to import. Click **Import**.

![Adobe I/O New Integration](./images/impconfirm.png)

You now have everything you need in Postman to start interacting with Adobe Experience Platform through the APIs.

The first thing to do, is to make sure you're properly authenticated. To be authenticated, you need to request an access token.

Make sure that you've got the right Environment selected before executing any request. You can check the currently selected Environment by verifying the Environment-dropdown list in the top right corner. 

The selected Environment should have a name similar to this one:

![Postman](./images/envselemea.png)

Click the **gear** icon to update the Private Key in the environment file.

![Postman](./images/gear.png)

Click the environment in the list:

![Postman](./images/pk1.png) 

You'll then see this. All fields are pre-populated, except for the field **PRIVATE_KEY**.

![Postman](./images/pk2.png)

The private key has been generated when you created your Adobe I/O Project. It was downloaded as a zip file, named **config.zip**. Extract that zip file to your desktop.

![Postman](./images/pk3.png)

Open the folder **config** and open the file **private.key** with your text editor of choice.

![Postman](./images/pk4.png)

You'll then see something resembling this, copy all the text to your clipboard.

![Postman](./images/pk5.png)

Go back to Postman and paste the private key in the fields next to the variable **PRIVATE_KEY**. Finally, click **Update**.

![Postman](./images/pk6.png)

Your Postman environment and collections are now configured and working. You can now authenticate from Postman to Adobe I/O.

To do that, you need to load an external library that will take care of the encryption and decryption of communication. To load this library, you have to execute the request with the name **INIT: Load Crypto Library for RS256**. Select this request in the **_Adobe I/O - Token collection** and you'll see it displayed in the middle of your screen.

![Postman](./images/iocoll.png)

![Postman](./images/cryptolib.png)

Click the blue **Send** button. After a couple of seconds, you should see a response displayed in the **Body** section of Postman:

![Postman](./images/cryptoresponse.png)

With the crypto library now loaded, we can authenticate to Adobe I/O.

In the **\_Adobe I/O - Token collection**, select the request with the name **IMS: JWT Generate + Auth**. Again, you'll see the request details displayed in the middle of the screen.

![Postman](./images/ioauth.png)

Click the blue **Send** button. After a couple of seconds, you should see a response displayed in the **Body** section of Postman:

![Postman](./images/ioauthresp.png)

If your configuration was successful, you should see a similar response that contains the following information:

| Key     | Value     | 
|:-------------:| :---------------:| 
| token_type          | **bearer** |
| access_token    | **eyJ4NXUiOiJpbXNfbmEx...QT7mqZkumN1tdsPEioOEl4087Dg** | 
| expires_in          | **86399973** |

Adobe I/O has given you a **bearer**-token, with a specific value (this very long access_token) and an expiration window.

The token that we've received is now valid for 24 hours. This means that after 24 hours, if you want to use Postman to authenticate to Adobe I/O, you will have to generate a new token by running this request again.

## Exercise 3.3 - Real-time Customer Profile API, Schema: Profile

Now you can go ahead and send your first request to Platform's Real-time Customer Profile APIs.

In Postman, locate the collection **_Adobe Experience Platform Enablement**.

![Postman](./images/coll_enablement.png)

In **1. Unified Profile Service**, select the first request with the name **UPS - GET Profile by Entity ID & NS**.

![Postman](./images/upscall.png)

For this request, there are three required variables:

| Key     | Value     | Definition |
|:-------------:| :---------------:| :---------------:| 
| entityId          | **id** | the specific customer ID |
| entityIdNS    | **namespace** | the specific namespace that is applicable to the ID |
| schema.name          | **_xdm.context.profile** | the specific schema for which you want to receive information |

So, if you want to ask Adobe Experience Platform's APIs to give you back all Profile information for your own ECID, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| entityId          | **yourECID** |
| entityIdNS    | **ecid** | 
| schema.name          | **_xdm.context.profile** |

![Postman](./images/callecid.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/callecidheaders.png)

| Key      | Value |
| ----------- | ----------- |
| x-sandbox-name      |`--aepSandboxId--`|

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. Your x-sandbox-name should be `--aepSandboxId--`.

Click **Send** to send your request to Platform.

You should get an immediate response from Platform, showing you something like this:

![Postman](./images/callecidresponse.png)

This is the full response from Platform:

```javascript
{
    "A29wOm-_HrdXL5njtUYzEOY7": {
        "entityId": "A29wOm-_HrdXL5njtUYzEOY7",
        "mergePolicy": {
            "id": "e9804b8f-a222-4b4f-9886-10437023eea6"
        },
        "sources": [
            "5fd1a9de42a61c194dd7b810",
            "profile-streaming-segment",
            "5fd1a9de241f58194b0cb117",
            ""
        ],
        "tags": [
            "710bd243-8559-4e5d-9345-ab85939ee234",
            "",
            "1607667023680:6739:84",
            "1607667488804:2012:187"
        ],
        "identityGraph": [
            "A29wOm-_HrdXL5njtUYzEOY7",
            "A2_bse0jTMN5DqeAHLrpovti",
            "CkF9rzLXMeI7bLh0LCef-IthzOCv71dY8wseCYosB3C73EMKhA",
            "BUF9zMKLrXq72p4HpbsHv1SCJHOaLTE1QGdtYWlsLmNvbQ",
            "BkFuK4QcJpSPByuCJHOaLTE1"
        ],
        "entity": {
            "_experienceplatform": {
                "identification": {
                    "core": {
                        "ecid": "34113965854450796644316155105296901017",
                        "phoneNumber": "+32473622044+10122020-15",
                        "email": "woutervangeluwe+10122020-15@gmail.com",
                        "emailIdSha256": "32d731e23b6cb8742c279ff88b61cce0ef5758f30b1e098a2c0770bbdc430a84"
                    }
                },
                "individualCharacteristics": {
                    "retail": {
                        "shirtSize": "L",
                        "favoriteColor": "black",
                        "shoeSize": "43"
                    },
                    "grocery": {
                        "allergies": {
                            "soy": false,
                            "dairy": false,
                            "gluten": false,
                            "nuts": false,
                            "shellfish": false
                        }
                    }
                },
                "loyaltyDetails": {
                    "level": "Bronze",
                    "points": 0.0
                },
                "demoEnvironment": {
                    "brandName": "Luma",
                    "ldap": "vangeluw",
                    "tms": "Launch"
                },
                "individualScoring": {
                    "churn": {
                        "churnPrediction": 0.15
                    }
                }
            },
            "personalEmail": {
                "address": "woutervangeluwe+10122020-15@gmail.com"
            },
            "_id": "5859709492881.192",
            "homeAddress": {
                "postalCode": "1831",
                "city": "Diegem",
                "country": "Belgium",
                "street1": "Culliganlaan 2a"
            },
            "mobilePhone": {
                "number": "+32473622044+10122020-15"
            },
            "optInOut": {
                "_channels": {
                    "directMail": "out",
                    "sms": "in",
                    "email": "in",
                    "phone": "in"
                }
            },
            "segmentMembership": {
                "ups": {
                    "207d9c3f-6513-474c-a300-5fbb2eb11f0b": {
                        "lastQualificationTime": "2020-12-10T23:29:21Z",
                        "status": "realized"
                    },
                    "97b66496-25fc-434b-92d4-df2155cddcaf": {
                        "lastQualificationTime": "2020-12-11T06:18:10Z",
                        "status": "existing"
                    },
                    "3a4ec8f1-5612-47b5-b58a-0b15a91cc7e6": {
                        "lastQualificationTime": "2020-12-11T06:06:20Z",
                        "status": "existing"
                    }
                }
            },
            "person": {
                "name": {
                    "lastName": "Van Geluwe",
                    "firstName": "Wouter"
                },
                "gender": "male",
                "birthDate": "1982-01-01"
            },
            "userActivityRegions": {
                "IRL1": {
                    "captureTimestamp": "2020-12-11T06:10:23Z"
                }
            },
            "profilePictureLink": "https://s7e4a.scene7.com/is/image/OmniPS/adobelogo?$fmt=alpha-png",
            "identityMap": {
                "ecid": [
                    {
                        "id": "10430795205006914197132473559604822183"
                    },
                    {
                        "id": "34113965854450796644316155105296901017"
                    }
                ],
                "email": [
                    {
                        "id": "woutervangeluwe+10122020-15@gmail.com"
                    }
                ],
                "email_lc_sha256": [
                    {
                        "id": "32d731e23b6cb8742c279ff88b61cce0ef5758f30b1e098a2c0770bbdc430a84"
                    }
                ],
                "phone": [
                    {
                        "id": "+32473622044+10122020-15"
                    }
                ]
            }
        },
        "lastModifiedAt": "2020-12-11T06:18:10Z"
    }
}
```

This is currently all of the available Profile data in Platform for this ECID.

You're not required to use the ECID to request Profile data from Platform's Real-time Customer Profile, you can use any ID in any namespace to request this data. 

Let's go back to Postman and pretend we're the call center, and send a request to Platform specifying the namespace of **Phone** and your mobile number.

So, if you want to ask Platform's APIs to give you back all Profile information for a specific Phone, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| entityId          | **your phone number** |
| entityIdNS    | **phone** (replace ecid by phone) | 
| schema.name          | **_xdm.context.profile** |

If your phone number contains special symbols like **+**, you have to select your full phone number, do a right-click and click **EncodeURIComponent**.

![Postman](./images/encodephone.png)

You'll then have this:

![Postman](./images/callmobilenr.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/callecidheaders.png)

| Key      | Value |
| ----------- | ----------- |
| x-sandbox-name      |`--aepSandboxId--`|

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. Your x-sandbox-name should be `--aepSandboxId--`.

Click the blue **Send** button and verify the response.

![Postman](./images/callmobilenrresponse.png)

Let's do the same thing for your email address by specifying the namespace of **email** and your email address.

So, if you want to ask Platform's APIs to give you back all Profile information for a specific email address, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| entityId          | **youremail** |
| entityIdNS    | **email** (replace Phone with email) | 
| schema.name          | **_xdm.context.profile** |

If your email address contains special symbols like **+**, you have to select your full email address, do a right-click and click **EncodeURIComponent**.

![Postman](./images/encodeemail.png)

You'll then have this:

![Postman](./images/callemail.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/callecidheaders.png)

| Key      | Value |
| ----------- | ----------- |
| x-sandbox-name      |`--aepSandboxId--`|

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. Your x-sandbox-name should be `--aepSandboxId--`.

Click the blue **Send** button and verify the response.

![Postman](./images/callemailresponse.png)

This is a very important kind of flexibility that is offered to brands. This means that any environment can send a request to Platform, using their own ID and namespace, without having to understand the complexity of multiple namespaces and IDs.

As an example:

* the Call Center will request data from Platform using the namespace **mobilenr**
* the Loyalty System will request data from Platform using the namespace **email**
* online applications might use the namespace **ecid**

The Call Center doesn't necessarily know what kind of identifier is used in the Loyalty System and the Loyalty System doesn't necessarily know what kind of identifier is used by online applications. Each individual system can use the information that they have and understand to get the information they need, when they need it.

## Exercise 3.3.4 - Real-time Customer Profile API, Schema: Profile and ExperienceEvent

After having queried Platform's APIs successfully for Profile data, let's now do the same with ExperienceEvent data.

In Postman, locate the collection **_Adobe Experience Platform Enablement**.

![Postman](./images/coll_enablement.png)

In **1. Unified Profile Service**, select the second request with the name **UPS - GET Profile & EE by Entity ID & NS**.

![Postman](./images/upseecall.png)

For this request, there are four required variables:

| Key     | Value     | Definition | 
|:-------------:| :---------------:|  :---------------:| 
| schema.name          | **_xdm.context.s** | the specific schema for which you want to receive information. In this case, we're looking for data that is mapped against the ExperienceEvent schema. | 
| relatedSchema.name          | **_xdm.context.profile** | While we're looking for data that is mapped against the ExperienceEvent schema, we need to specify an identity for which we want to receive that data. The schema that has access to identity is the Profile-schema, so the relatedSchema here is the Profile-schema. |
| relatedEntityId          | **id** | the specific customer I D|
| relatedEntityIdNS    | **namespace** | the specific namespace that is applicable to the ID | 

So, if you want to ask Platform's APIs to give you back all Profile information for your own ecid, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| schema.name          | **_xdm.context.experienceevent** |
| relatedSchema.name          | **_xdm.context.profile** |
| relatedEntityId          | **yourECID** |
| relatedEntityIdNS    | **ecid** | 

![Postman](./images/eecallecid.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/eecallecidheaders.png)

| Key      | Value |
| ----------- | ----------- |
| x-sandbox-name      |`--aepSandboxId--`|

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. Your x-sandbox-name should be `--aepSandboxId--`.

Click **Send** to send your request to Platform.

You should get an immediate response from Platform, showing you something like this:

![Postman](./images/eecallecidresponse.png)

Below is the full response from Platform. In this example, there are eight ExperienceEvents linked to this customer's ECID. Have a look at the below to see the different variables on the request, as what you see below is the direct consequence of your configuration in Launch in previous exercises.

Also, when the X-ray panel shows ExperienceEvent information, it is using the below payload to parse and retrieve the information like Product Name (search for productName in the below payload) and Product Image URL (search for productImageUrl in the below payload).

```javascript
{
    "_page": {
        "orderby": "timestamp",
        "start": "710bd243-8559-4e5d-9345-ab85939ee234-0",
        "count": 44,
        "next": ""
    },
    "children": [
        {
            "relatedEntityId": "A29wOm-_HrdXL5njtUYzEOY7",
            "entityId": "710bd243-8559-4e5d-9345-ab85939ee234-0",
            "timestamp": 1607634623789,
            "entity": {
                "environment": {
                    "ipV4": "213.118.237.49",
                    "type": "browser",
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 11_0_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36",
                        "acceptLanguage": "en",
                        "viewportHeight": 969.0,
                        "viewportWidth": 1920.0
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Luma Home",
                        "URL": "https://public.aepdemo.net/index.html"
                    },
                    "webReferrer": {
                        "URL": "https://public.aepdemo.net/admin.html"
                    }
                },
                "_experienceplatform": {
                    "demoEnvironment": {
                        "brandIndustry": "retail",
                        "brandName": "Luma",
                        "tms": "Launch",
                        "brandLogo": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/d632e769791f0a4dbe0b84058d282d45_logo.png",
                        "ldap": "vangeluw"
                    },
                    "identification": {
                        "core": {
                            "ecid": "34113965854450796644316155105296901017"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.3.0+2.2.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "CORE": [
                        {
                            "id": "34343827312771250614258373109911428140",
                            "authenticatedState": "ambiguous",
                            "primary": false
                        }
                    ],
                    "ECID": [
                        {
                            "id": "34113965854450796644316155105296901017",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "710bd243-8559-4e5d-9345-ab85939ee234-0",
                "placeContext": {
                    "localTime": "2020-12-10T22:10:23.789+01:00",
                    "localTimezoneOffset": -60.0
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920.0,
                    "screenHeight": 1080.0
                },
                "timestamp": "2020-12-10T21:10:23.789Z"
            },
            "lastModifiedAt": "2020-12-10T21:10:25Z"
        },
        {
            "relatedEntityId": "A29wOm-_HrdXL5njtUYzEOY7",
            "entityId": "c02b8be3-b220-4c2b-92fd-96ac7f5aa3f4-0",
            "timestamp": 1607639281610,
            "entity": {
                "environment": {
                    "ipV4": "213.118.237.49",
                    "type": "browser",
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 11_0_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36",
                        "acceptLanguage": "en",
                        "viewportHeight": 1001.0,
                        "viewportWidth": 1920.0
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Luma Home",
                        "URL": "https://public.aepdemo.net/index.html"
                    },
                    "webReferrer": {
                        "URL": "https://public.aepdemo.net/admin.html"
                    }
                },
                "_experienceplatform": {
                    "demoEnvironment": {
                        "brandIndustry": "retail",
                        "brandName": "Luma",
                        "tms": "Launch",
                        "brandLogo": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/d632e769791f0a4dbe0b84058d282d45_logo.png",
                        "ldap": "vangeluw"
                    },
                    "identification": {
                        "core": {
                            "ecid": "34113965854450796644316155105296901017"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.3.0+2.2.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "34113965854450796644316155105296901017",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "c02b8be3-b220-4c2b-92fd-96ac7f5aa3f4-0",
                "placeContext": {
                    "localTime": "2020-12-10T23:28:01.610+01:00",
                    "localTimezoneOffset": -60.0
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920.0,
                    "screenHeight": 1080.0
                },
                "timestamp": "2020-12-10T22:28:01.610Z"
            },
            "lastModifiedAt": "2020-12-10T22:28:03Z"
        },
        {
            "relatedEntityId": "A29wOm-_HrdXL5njtUYzEOY7",
            "entityId": "db1f1dca-5882-4b99-95af-8fe18f8bb663-0",
            "timestamp": 1607639409017,
            "entity": {
                "environment": {
                    "ipV4": "213.118.237.49",
                    "type": "browser",
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 11_0_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36",
                        "acceptLanguage": "en",
                        "viewportHeight": 1001.0,
                        "viewportWidth": 1920.0
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Nadia Elements Shell",
                        "URL": "https://public.aepdemo.net/p1.html"
                    },
                    "webReferrer": {
                        "URL": "https://public.aepdemo.net/index.html"
                    }
                },
                "_experienceplatform": {
                    "demoEnvironment": {
                        "brandIndustry": "retail",
                        "brandName": "Luma",
                        "tms": "Launch",
                        "brandLogo": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/d632e769791f0a4dbe0b84058d282d45_logo.png",
                        "ldap": "vangeluw"
                    },
                    "identification": {
                        "core": {
                            "ecid": "34113965854450796644316155105296901017"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.3.0+2.2.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "34113965854450796644316155105296901017",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "commerce.productViews",
                "_id": "db1f1dca-5882-4b99-95af-8fe18f8bb663-0",
                "commerce": {
                    "productViews": {
                        "value": 1.0
                    }
                },
                "productListItems": [
                    {
                        "product": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg",
                        "quantity": 1.0,
                        "productAddMethod": "Desktop",
                        "_experienceplatform": {
                            "core": {
                                "productURL": "https://public.aepdemo.net/p1.html",
                                "imageURL": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg"
                            }
                        },
                        "priceTotal": 69.0,
                        "name": "Nadia Elements Shell",
                        "SKU": "LLWJ10.1-XS"
                    }
                ],
                "placeContext": {
                    "localTime": "2020-12-10T23:30:09.017+01:00",
                    "localTimezoneOffset": -60.0
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920.0,
                    "screenHeight": 1080.0
                },
                "timestamp": "2020-12-10T22:30:09.017Z"
            },
            "lastModifiedAt": "2020-12-10T22:30:10Z"
        },
        {
            "relatedEntityId": "A29wOm-_HrdXL5njtUYzEOY7",
            "entityId": "eab8818b-438a-4e4e-8129-ac7adc0b6d2a-0",
            "timestamp": 1607639509214,
            "entity": {
                "environment": {
                    "ipV4": "213.118.237.49",
                    "type": "browser",
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 11_0_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36",
                        "acceptLanguage": "en",
                        "viewportHeight": 1001.0,
                        "viewportWidth": 1920.0
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Luma Home",
                        "URL": "https://public.aepdemo.net/index.html"
                    },
                    "webReferrer": {
                        "URL": "https://public.aepdemo.net/p1.html"
                    }
                },
                "_experienceplatform": {
                    "demoEnvironment": {
                        "brandIndustry": "retail",
                        "brandName": "Luma",
                        "tms": "Launch",
                        "brandLogo": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/d632e769791f0a4dbe0b84058d282d45_logo.png",
                        "ldap": "vangeluw"
                    },
                    "identification": {
                        "core": {
                            "ecid": "34113965854450796644316155105296901017"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.3.0+2.2.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "34113965854450796644316155105296901017",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "eab8818b-438a-4e4e-8129-ac7adc0b6d2a-0",
                "placeContext": {
                    "localTime": "2020-12-10T23:31:49.214+01:00",
                    "localTimezoneOffset": -60.0
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920.0,
                    "screenHeight": 1080.0
                },
                "timestamp": "2020-12-10T22:31:49.214Z"
            },
            "lastModifiedAt": "2020-12-10T22:31:50Z"
        },
        {
            "relatedEntityId": "A29wOm-_HrdXL5njtUYzEOY7",
            "entityId": "63996797-d4ad-46e4-95d2-0a32a687295d-0",
            "timestamp": 1607639513538,
            "entity": {
                "environment": {
                    "ipV4": "213.118.237.49",
                    "type": "browser",
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 11_0_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36",
                        "acceptLanguage": "en",
                        "viewportHeight": 1001.0,
                        "viewportWidth": 1920.0
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Radiant Tee - (Orange)",
                        "URL": "https://public.aepdemo.net/p4.html"
                    },
                    "webReferrer": {
                        "URL": "https://public.aepdemo.net/index.html"
                    }
                },
                "_experienceplatform": {
                    "demoEnvironment": {
                        "brandIndustry": "retail",
                        "brandName": "Luma",
                        "tms": "Launch",
                        "brandLogo": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/d632e769791f0a4dbe0b84058d282d45_logo.png",
                        "ldap": "vangeluw"
                    },
                    "identification": {
                        "core": {
                            "ecid": "34113965854450796644316155105296901017"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.3.0+2.2.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "34113965854450796644316155105296901017",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "commerce.productViews",
                "_id": "63996797-d4ad-46e4-95d2-0a32a687295d-0",
                "commerce": {
                    "productViews": {
                        "value": 1.0
                    }
                },
                "productListItems": [
                    {
                        "product": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/58ae7e91a9bac17cdf92a178d6e25186_1.jpg",
                        "quantity": 1.0,
                        "productAddMethod": "Desktop",
                        "_experienceplatform": {
                            "core": {
                                "productURL": "https://public.aepdemo.net/p4.html",
                                "imageURL": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/58ae7e91a9bac17cdf92a178d6e25186_1.jpg"
                            }
                        },
                        "priceTotal": 22.0,
                        "name": "Radiant Tee - (Orange)",
                        "SKU": "LUMA-24-CXV14"
                    }
                ],
                "placeContext": {
                    "localTime": "2020-12-10T23:31:53.538+01:00",
                    "localTimezoneOffset": -60.0
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920.0,
                    "screenHeight": 1080.0
                },
                "timestamp": "2020-12-10T22:31:53.538Z"
            },
            "lastModifiedAt": "2020-12-10T22:31:54Z"
        },
    ],
    "_links": {
        "next": {
            "href": ""
        }
    }
}
```

This is currently all of the available ExperienceEvent data in Platform for this ECID.

You're not required to use the ECID to request ExperienceEvent data from Adobe Experience Platform's Real-time Profile, you can use any ID in any namespace to request this data. 

Next Step: [3.4 Create a segment - UI](./ex4.md)

[Go Back to Module 3](./real-time-customer-profile.md)

[Go Back to All Modules](../../overview.md)
