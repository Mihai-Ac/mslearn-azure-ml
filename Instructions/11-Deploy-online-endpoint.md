---
lab:
    title: 'Deploy a model to a managed online endpoint'
---

# Deploy a model to a managed online endpoint

To consume a model in an application, and get real-time predictions, you'll want to deploy the model to a managed online endpoint. An MLflow model is easily deployed since you won't need to define the environment or create the scoring script.

In this exercise, you'll deploy an MLflow model to a managed online endpoint, and test it on sample data. 

## Before you start

You'll need an [Azure subscription](https://azure.microsoft.com/free?azure-portal=true) in which you have administrative-level access.

## Provision an Azure Machine Learning workspace

An Azure Machine Learning *workspace* provides a central place for managing all resources and assets you need to train and manage your models. You can interact with the Azure Machine Learning workspace through the studio, Python SDK, and Azure CLI. 

You'll use the Azure CLI to provision the workspace and necessary compute, and you'll use the Python SDK to run a command job.

### Create the workspace and compute resources

To create the Azure Machine Learning workspace, a compute instance, and a compute cluster, you'll use the Azure CLI. All necessary commands are grouped in a Shell script for you to execute.

1. In a browser, open the Azure portal at `https://portal.azure.com/`, signing in with your Microsoft account.
1. Select the \[>_] (*Cloud Shell*) button at the top of the page to the right of the search box. This opens a Cloud Shell pane at the bottom of the portal.
1. Select **Bash** if asked. The first time you open the cloud shell, you will be asked to choose the type of shell you want to use (*Bash* or *PowerShell*). 
1. Check that the correct subscription is specified and select **Create storage** if you are asked to create storage for your cloud shell. Wait for the storage to be created.
1. In the terminal, enter the following commands to clone this repo:

    ```bash
    rm -r azure-ml-labs -f
    git clone https://github.com/MicrosoftLearning/mslearn-azure-ml.git azure-ml-labs
    ```

    > Use `SHIFT + INSERT` to paste your copied code into the Cloud Shell. 

1. After the repo has been cloned, enter the following commands to change to the folder for this lab and run the **setup.sh** script it contains:
    
    ```bash
    cd azure-ml-labs/Labs/11
    ./setup.sh
    ```

    > Ignore any (error) messages that say that the extensions were not installed. 

1. Wait for the script to complete - this typically takes around 5-10 minutes. 

## Clone the lab materials

When you've created the workspace and necessary compute resources, you can open the Azure Machine Learning studio and clone the lab materials into the workspace. 

1. In the Azure portal, navigate to the Azure Machine Learning workspace named **mlw-dp100-labs**.
1. Select the Azure Machine Learning workspace, and in its **Overview** page, select **Launch studio**. Another tab will open in your browser to open the Azure Machine Learning studio.
1. Close any pop-ups that appear in the studio.
1. Within the Azure Machine Learning studio, navigate to the **Compute** page and verify that the compute instance and cluster you created in the previous section exist. The compute instance should be running, the cluster should be idle and have 0 nodes running.
1. In the **Compute instances** tab, find your compute instance, and select the **Terminal** application.
1. In the terminal, install the Python SDK on the compute instance by running the following commands in the terminal:
    
    ```
    pip uninstall azure-ai-ml
    pip install azure-ai-ml
    ```

    > Ignore any (error) messages that say that the packages couldn't be found and uninstalled.

1. Run the following command to clone a Git repository containing a notebook, data, and other files to your workspace:
    
    ```
    git clone https://github.com/MicrosoftLearning/mslearn-azure-ml.git azure-ml-labs
    ```
 
1. When the command has completed, in the **Files** pane, click **&#8635;** to refresh the view and verify that a new **Users/*your-user-name*/azure-ml-labs** folder has been created. 

## Deploy a model to an online endpoint

The code to create the endpoint and deploy an MLflow model with the Python SDK is provided in a notebook. 

1. Open the **Labs/11/Deploy to online endpoint.ipynb** notebook.

    > Select **Authenticate** and follow the necessary steps if a notification appears asking you to authenticate. 

1. Verify that the notebook uses the **Python 3.8 - AzureML** kernel. 
1. Run all cells in the notebook.

## Delete Azure resources

When you finish exploring Azure Machine Learning, you should delete the resources you've created to avoid unnecessary Azure costs.

1. Close the Azure Machine Learning studio tab and return to the Azure portal.
1. In the Azure portal, on the **Home** page, select **Resource groups**.
1. Select the **rg-dp100-labs** resource group.
1. At the top of the **Overview** page for your resource group, select **Delete resource group**. 
1. Enter the resource group name to confirm you want to delete it, and select **Delete**.