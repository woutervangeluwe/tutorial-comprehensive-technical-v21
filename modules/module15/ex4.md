---
title: Data Science Workspace - Train and Score your Recipe
description: Data Science Workspace - Train and Score your Recipe
kt: 5342
audience: Data Engineer, Data Architect, Data Scientist
doc-type: tutorial
activity: develop
exl-id: 9a86934a-13ac-44df-8f1e-c7b6b934e6d1
---
# 15.4 Train and Score your Recipe

After creating a recipe, you can now train and score your recipe without having to touch code again.

## 15.4.1 Train a Model based on a Recipe

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)

From the left menu, click **Models**.

![DSW](./images/mlmodels.png)

In this exercise, you'll use a prebuilt recipe to create a Model for Car Insurance Sales Predictions.

In the top menu, click on **Recipes**.

![DSW](./images/recipes.png)

In Recipes, you'll find multiple recipes. Look for your own recipe in the list, which should be named `ldapCarInsurancePropensity`.

![DSW](./images/prrecipe.png)

Click the `ldapCarInsurancePropensity` recipe to open it.

![DSW](./images/prrecipe1.png)

You now need to create your own Model, based on the `ldapCarInsurancePropensity` recipe.

To do that, click on the **Create a Model** button.

![DSW](./images/createmodel1.png)

To train this model, you need to provide it with an Input Dataset. In our case, the dataset to use is called `Demo System - Event Dataset for Website (Global v1.1)`. Select it from the list.

![DSW](./images/input.png)

Click **Next** to continue.

![DSW](./images/next.png)

In the next step, you need to define a name for your Model. As a naming convention, let's use: `ldap -  CarInsurancePropensity Model` and replace `ldap` with your ldap.

Example: for ldap vangeluw, the name becomes `vangeluw - CarInsurancePropensity Model`.

![DSW](./images/modelname.png)

You can also hyper-tune the Model by changing the Model Configuration. To do that, you can for instance change the **n_estimators** or the **max_depth**.

![DSW](./images/modelcfg.png)

If you want to update the Model's Configuration parameters, double-click one of the parameters and give it a new value.

Next, click **Finish** to finish your configuration.

![DSW](./images/finish.png)

After a couple of seconds, you'll be reverted back to the Model's homepage where you'll see a Training Run 1 with a status of **Pending**. The process to finish the training run can take 5+ minutes.

![DSW](./images/trainingrunp.png)

After 1-2 minutes, your Training Run's status will change to **Running**.

![DSW](./images/trainingrunrunning.png)

And 1-2 minutes later, the Training Run's status will change to **Complete**.

![DSW](./images/trainingrunsuccess.png)

Once the Training Run has completed, you'll see an Accuracy Metric that indicates how successful the model is. (Due to the lack of training data, accuracy doesn't say much in this demo situation).
  
![DSW](./images/acc.png)

Training a model requires more than one run. All Training Runs will be visible on this page and you'll be able to compare their results, so you can decide which one is the most successful.
![DSW](./images/multipleruns.png)

## 15.4.2 Score a Model based on a Recipe

After training a model, you can use the model to score and as such, have the model calculate Car Insurance Sales Propensity scores which can be activated through targeting.

To start scoring, let's re-open Training Run 1 by clicking it.

![DSW](./images/trainingrunsuccess.png)

After opening Training Run 1, you'll see a full overview of the Training Run, and in the future, more visualization options will be added.

![DSW](./images/trr1.png)

To score, you have to click the **+ Score** button in the top right corner of your screen.

![DSW](./images/score.png)

In the next step, you again have to select an Input Dataset. Let's choose the `Demo System - Event Dataset for Website (Global v1.1)` dataset.

![DSW](./images/scoreinput.png)

After selecting the Input Dataset, click **Next**.

![DSW](./images/next.png)

In the next step, you need to select a dataset to which Platform will output results. In this case, select the `Demo System - Profile Dataset for ML Predictions (Global v1.1)` dataset.

![DSW](./images/scoreoutput.png)

After selecting the Output Dataset, click **Next**.

![DSW](./images/next.png)

In the next screen, you can again specify/change some of the Model's Configuration parameters.

![DSW](./images/scoreconfig.png)

After updating the Model's Configuration parameters, click **Finish**.

![DSW](./images/finish.png)

A **Scoring Run** is now created, and has a status of **Pending**, which will change to **Running**.

![DSW](./images/scoringrunp.png)
![DSW](./images/scoringrunr.png)

And 1-2 minutes later, the Scoring Run's status will change to **Complete**.

![DSW](./images/scoringrunsuccess.png)

And finally, let's preview the results. Click on **Scoring Run 1**

![DSW](./images/scoringrunsuccessdtl.png)

Next, click the **Preview Scoring Results Dataset**.

![DSW](./images/preview.png)

![DSW](./images/previewresults.png)

Click **Close** to close the Preview Scoring Results window.

Next Step: [15.5 Publish your Recipe as a Scheduled Service](./ex5.md)

[Go Back to Module 15](./data-science-workspace-car-insurance-sales-propensity.md)

[Go Back to All Modules](../../overview.md)
