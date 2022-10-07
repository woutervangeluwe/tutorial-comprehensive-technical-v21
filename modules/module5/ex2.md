---
title: Extract, Transform, Load data using a 3rd party ETL-tool - Setup an AWS S3 bucket
description: Extract, Transform, Load data using a 3rd party ETL-tool - Setup an AWS S3 bucket
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 859bd528-710c-4b47-9930-ae79e82442e3
---
# 5.2 Setup an AWS S3 bucket

In this exercise, you'll learn how to setup an AWS S3 bucket in your own AWS environment and how to upload data in that S3 bucket.

First of all, in this module we'll use four CSV files as datasources in Informatica. Please download the file **csvfiles.zip** here: [CSV files](./../../assets/csv/module5/csvfiles.zip)

![ETL](./images/csv.png)

## Create your S3 bucket

Go to [https://console.aws.amazon.com](https://console.aws.amazon.com) and sign in with the Amazon-account you created in Module 4.

![ETL](./images/awshome.png)

After logging in, you'll be redirected to the **AWS Management Console**.

![ETL](./images/awsconsole.png)

In the **Find Services** menu, search for **s3**.

![ETL](./images/awsconsoles3.png)

Click the first search result: **S3 - Scalable Storage in the Cloud**.

You'll then see the **Amazon S3** homepage.

![ETL](./images/s3home.png)

Click the **Create Bucket** button.

![ETL](./images/createbucket.png)

In the **Create Bucket** screen, you need to configure two things:
  
- Name: use the name **aepmodule5LDAP** and replace LDAP by your LDAP. As an example, in this exercise the bucket name is **aepmodule5vangeluw**
- Region: use the region **EU (Frankfurt) eu-central-1**

![ETL](./images/bucketname.png)

Scroll down on the page until you see **Bucket settings for Block Public Access**. Leave these settings as they are, no need to change them.

![ETL](./images/bucketsett.png)

Click the **Create Bucket** button.

![ETL](./images/createbucket.png)

You'll then see your bucket being created and will be redirected to the Amazon S3 homepage.

![ETL](./images/S3homeb.png)

### Upload CSV files to your S3 bucket

The next step is to upload the CSV files we'll use for this module into your S3 bucket.

Click on your S3 bucket to open it. You'll then see this page.

![ETL](./images/s3up.png)

Click **Upload** to start uploading the four CSV files.

![ETL](./images/upload.png)

You'll then see this popup.

![ETL](./images/upload1.png)

Click **Add Files**.

![ETL](./images/addfiles.png)

Navigate to the directory **csvfiles** on your desktop, select all four files and then click **Open**.

![ETL](./images/selectfiles.png)

You'll then see this screen.

![ETL](./images/selectfilesok.png)

Click **Upload**.

![ETL](./images/upload.png)

You'll now see your CSV files uploaded in your S3 bucket.

![ETL](./images/s3csv.png)

### Set permissions to access your S3 bucket

The next step is to setup access to your S3 bucket.

To do that, go to [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home).

Access to AWS resources is controlled by Amazon Identity and Access Management (IAM).

You'll now see this page.

![ETL](./images/iam.png)

In the left menu, click **Users**.

![ETL](./images/iammenu.png)

You'll then see the **Users** screen.

![ETL](./images/users.png)

Click **Add User**.

![ETL](./images/adduser.png)

Next, configure your user:

- User Name: use **s3_ldap** as a name, so in this example the name is **s3_vangeluw**.
- AWS access type: select **Programmatic access**.

    ![ETL](./images/configuser.png)

Click **Next: Permissions**.

![ETL](./images/nextperm.png)

You'll then see this permissions screen. Click **Attach existing policies directly**.

![ETL](./images/perm1.png)

Enter the search term **s3** to see all related S3 policies. Select the policy **AmazonS3FullAccess**.

![ETL](./images/perm2.png)

Click **Next: Tags**.

![ETL](./images/nexttags.png)

On the **Tags** screen, there's no need to configure anything.

![ETL](./images/perm3.png)

Click **Next: Review**.

Review your configuration.

![ETL](./images/review.png)

Click **Create User**.

Your user is now created and you're seeing your Credentials to access your S3 environment. This is the only time you'll see your credentials so please write them down.

![ETL](./images/cred.png)

Click **Show** to see your Secret access key:

![ETL](./images/cred1.png)

>[!IMPORTANT]
>
>Store your credentials in a text-file in your computer.
>
> - Access key ID: ...
> - Secret access key: ...
>
> Once you click **Close** you'll never see your credentials again!

Click **Close**. 

![ETL](./images/close.png)

You've now successfully created an AWS S3 bucket, you've uploaded CSV files into that bucket and you've created a user with permissions to access this bucket.

Next Step: [5.3 Connect Informatica to your AWS S3 bucket](./ex3.md)

[Go Back to Module 5](./data-ingestion-informatica-etl.md)

[Go Back to All Modules](../../overview.md)
