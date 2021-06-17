# Automate model building with AutoAI

In this module, we'll learn how to use [AutoAI](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/autoai-overview.html?audience=wdp). The AutoAI tool is a capability that automates various tasks to ease the workflow for data scientists that are creating machine learning models. AutoAI automatically analyzes your data and generates candidate model pipelines customized for your predictive modeling problem.  These model pipelines are created iteratively as AutoAI analyzes your dataset and discovers data transformations, algorithms, and parameter settings that work best for your problem setting.

This section is broken up into the following steps:

1. [Run AutoAI Experiment](#create-an-autoai-experiment)
1. [Save and Promote AutoAI Model](#save-and-promote-autoai-model)
1. [Save AutoAI Notebooks](#save-autoai-notebooks)
1. [Conclusion](#conclusion)

> **Note:** You can click on any image in the instructions below to zoom in and see more details. When you do that just click on your browser's back button to return to the previous page.

## Create an AutoAI Experiment

* Go the (☰) navigation menu, expand `Projects` and click on the project you created during the setup section.

    [![(☰) Menu -> your project](../images/navigation/menu-projects.png)](../images/navigation/menu-projects.png)

* To start the AutoAI experiment, click the `Add to project +` button from the top of the page and select the `AutoAI experiment` option.

    [![Adding a project](../images/autoai/autoai-add-project.png)](../images/autoai/autoai-add-project.png)

* Give the AutoAI experiment any name you like. The associated Watson Machine Learning Service Instance should already be populated for you. If not, please select the one that you created in the setup section from the drop down. Then click the `Create` button.

    [![Naming your experiment](../images/autoai/autoai-name-experiment.png)](../images/autoai/autoai-name-experiment.png)

* To configure the experiment, we must first give it the dataset that will be used to train the machine learning model. Click on the `Select from project` button to point to a dataset in your project.

* Now we can select the training CSV file. If you completed the previous ***Data Processing with Data Refinery*** lab module where you generated a single shaped CSV file from a refinery job, select that CSV file (the name will be whatever you selected in that module, for example: `incident_shaped.csv`).

    [![Select data](../images/autoai/autoai-select-dataset.png)](../images/autoai/autoai-select-dataset.png)

* Now, we will need to indicate what we want the model to predict. Under `What do you want to predict?` panel, select the `Prediction column` as `inc_business_duration`.

* AutoAI will set up defaults values for the experiment based on the dataset and the column selected for the prediction. This includes the type of model to build, the metrics to optimize against, the test/train split, etc. To view/change these values, click the *`Experiment settings`* button.

    [![Choose Churn column and run](../images/autoai/autoai-choose-prediction-and-configure.png)](../images/autoai/autoai-choose-prediction-and-configure.png)

* Click on the `Data source` tab. For the sake of time, in the `Subsample` section turn on `Subsample rows` switch and set the `Amount` to 10 percent. Scroll down to the `Select features to include` section. Deselect the checkbox for the `number`, `taskslatable_sla`, `taskslatable_stage`, `inc_calendar_duration`, `taskslatable_start_time` and `taskslatable_end_time` column names. This will remove these fields from being used as a feature for the model. Although we could change other aspects of the experiment, we will accept the remaining default values and click the `Save settings` button. (*Feel free to explore the other possible settings before clicking the save button*).

    [![Choose features and save](../images/autoai/autoai-exp-settings-sample.png)](../images/autoai/autoai-exp-settings-sample.png)

    [![Choose features and save](../images/autoai/autoai-exp-settings-columns-1.png)](../images/autoai/autoai-exp-settings-columns-1.png)

    [![Choose features and save](../images/autoai/autoai-exp-settings-columns-2.png)](../images/autoai/autoai-exp-settings-columns-2.png)


* To start the experiment, click on the `Run experiment` button.

    [![Run experiment](../images/autoai/autoai-exp-run.png)](../images/autoai/autoai-exp-run.png)

* The AutoAI experiment will now run. AutoAI will run through steps to prepare the dataset, split the dataset into training / evaluation groups and then find the best performing algorithms / estimators for the type of model. It will then build the following series of candidate pipelines for each of the top N performing algorithms (where N is a number chosen in the configuration which defaults to 2):

    * Baseline model (Pipeline 1)
    * Hyperparameter optimization (Pipeline 2)
    * Automated feature engineering (Pipeline 3)
    * Hyperparameter optimization on top of engineered features (Pipeline 4)

* The UI will show progress as different algorithms/evaluators are selected and as different pipelines are created and evaluated. You can view the performance of the pipelines that have completed by expanding each pipeline section in the leaderboard.

    [![autoai progress](../images/autoai/autoai-pipeline-progress.png)](../images/autoai/autoai-pipeline-progress.png)

* The experiment can take several minutes to complete. Upon completion you will see a message that the pipelines have been created. Do not proceed to the next section until the experiment completes.

## Save and Promote AutoAI Model

* Once the experiment completes, you can explore the various pipelines and options in the UI. Some of the options available are to see a comparison of the pipelines, to change the ranking based on a different performance metric, to see a log of the experiment, or to see the ranked listing of the pipelines (ranking based on the optimization metric in your experiment, in this case, RMSE).

    [![autoai pipelines created](../images/autoai/autoai-pipelines-complete.png)](../images/autoai/autoai-pipelines-complete.png)

* Scroll down to see the `Pipeline leaderboard`. The top performing pipeline is in the first rank.

* The next step is to select the model that gives the best result and view its performance. In this case, Pipeline 4 gave the best result for our experiment. You can view the detailed results by clicking the corresponding pipeline name from the leaderboard:

    [![pipeline leaderboard](../images/autoai/autoai-pipeline-leaderboard-topranked.png)](../images/autoai/autoai-pipeline-leaderboard-topranked.png)

* The model evaluation page will show metrics for the experiment, feature transformations that were performed (if any), which features contribute to the model, and more details of the pipeline. Optionally, feel free to click through these views of the pipeline details. For instance, you could select `Pipeline 2` (before the feature engineering step) and review the `Feature Importance` tab. You will notice that `assignment_group` is the on the top of this list

    [![Model evaluation](../images/autoai/autoai-toppipeline-details.png)](../images/autoai/autoai-toppipeline-details.png)

* In order to deploy this model, select `Pipeline 4`,  click on the *`Save as`* button. On the next scren, select the `Model` option. Keep the default name, add an optional description and tags, and click the `Create` button to save the model.

    ![Save model](../images/autoai/autoai-pipeline-save-model.png)

* You will see a notification to indicate that your model is saved to your project. Click the `View in project` link in the notification to go to the saved model. (*Alternatively, if you navigate back to your project assets tab by closing the pipeline and AutoAI experiment, you will see the saved model in the `Models` section, which you can click on to explore*).

    ![Go to model](../images/autoai/autoai-save-notification.png)

* To make the model available to be deployed, we need to make it available in the deployment space you created during the setup module. Click on the `Promote to deployment space`:

    [![Deploying the model](../images/autoai/autoai-promote-to-space.png)](../images/autoai/autoai-promote-to-space.png)

* Select the deployment space that was created as part of the setup module as the `Target space` and click `Promote`.

    [![Promote model](../images/autoai/autoai-promote-to-space-confirm.png)](../images/autoai/autoai-promote-to-space-confirm.png)

* You will be brought back to your project assets page and see a notification that the model was promoted to the deployment space successfully. Feel free to close that notification.


## Conclusion

Congratulation. We have now successfully created a highly optimized machine learning model using AutoAI and prepared it for deployment.

In this section we covered one approach to building machine learning models on Cloud Pak for Data as a Service. We have seen how AutoAI helps to find an optimal model by automating tasks such as:

* Data Wrangling
* Algorithm Evaluation & Selection
* Feature Engineering
* Hyperparameter Optimization
