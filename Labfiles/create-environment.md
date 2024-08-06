# Lab 4: GitHub Environment

GitHub environments are a feature in GitHub Actions that allow you to define and manage different deployment environments, such as development, staging, and production. Environments can include protection rules like required reviewers, wait times, and environment-specific secrets to enhance security and control. This feature helps ensure that deployments are carried out in a controlled and consistent manner, providing safeguards and configurable policies for each stage of your deployment process.

In this exercise, you'll learn how to set up environments with protection rules, wait timers, environment secrets, and variables. A workflow job that references an environment must adhere to these protection rules before it can run or access the environment's secrets.

## Task 1: Set up Environment

In this task, you'll set up a GitHub environment and use it as a GitHub action.

1. In the GitHub dashboard, navigate to the **Settings (1)** tab. Select **Environments (2)**, and click on **New Environment (3)**.

   ![](../media/env1.png) 

1. Follow the steps mentioned below and create the environment. 

**Required Reviewers**
   - Provide the name as **action-environment** and click on **configure environment**.
     ![](../media/configure_env1.png) 

   - In the **Deployment protection rules** section, check the **Required reviewers** option. Search for the **GitHub username**, and add the user. You can also find the username on the **GitHub homepage**.

**Wait Timer**
   - Select the **Wait timer (2)** check box and set it to 2 minutes.

     ![](../media/env2(1).png)

     - Click on **Save protection rules** to save the rules.

     ![](../media/env39.png)

   - Now, scroll down to **Environment Secrets** and click on **Add environment secret**.

     ![](../media/env9.png)

   **Environment Secrets**

   - Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret (3)**.

   - Copy and paste the code below in the value section.
   
      ```json
      {
        "clientSecret": "******",
        "subscriptionId": "******",
        "tenantId": "******",
        "clientId": "******"
      }
      ```

   - Navigate to the **Environment** **(1)** tab. Click on **Service Principal Details** **(2)** and copy the **Subscription ID (4)**, **Tenant Id (Directory ID) (5)**, **Application Id (Client Id) (6),** and **Secret Key (Client Secret) (3)**.

     ![](../media/ex2-t4-8.png)

   - Name: Enter **AZURE_CREDENTIALS** **(1)**
   - Value: Paste the service principal details in **JSON format (2)**. Click on **Add secret (3)**.

     ![](../media/env10(1).png)

**Environment Variable**

   - Navigate to the **Azure portal** and select your container instance, **gacontiner<inject key="DeploymentID" enableCopy="false"/>**, which you deployed in the earlier exercise.

   - Click on **Access Keys** **(1)** on the left pane under the **Settings** tab and copy the **Registry name** **(2)** and **Login server** **(3)** initials into a notepad.

     ![](../media/access-keys.png)

   - Navigate back to the GitHub dashboard. Under the **Environment variables** section, click on **Add environment variable**.
   
     ![](../media/env11.png)

   - Provide the name as **REGISTRY_NAME (1)**, paste the **value (2)** you copied from in earlier steps, and click on **Add Variable (3)**.

     ![](../media/env40.png)

   - Similarly, click again on the **Add environment variable**. Provide the name as **LOGIN_SERVER (1)** and paste the **login server value (2)** copied in earlier steps. Finally, click on **Add varianble (3)**.

     ![](../media/env41.png)

   - Please make sure that you've completed all the steps for creating a GitHub Environment. 

**Creating Workflow with the Environment**

1. Visit the GitHub home page, navigate to `.github/workflows/docker.yml` file, and update the script as provided below.

    ```
    name: Build and Push Docker Image to ACR
    
    on:
      push:
        branches:
          - main
        paths:
          - '.github/workflows/docker.yml'
      pull_request:
        branches:
          - main
        paths:
          - '.github/workflows/docker.yml'
      workflow_dispatch:
    
    jobs:
      build-and-push:
        environment: action-environment
        runs-on: ubuntu-latest
    
        steps:
        # Checkout the repository
        - name: Checkout repository
          uses: actions/checkout@v2
    
        # Log in to Azure
        - name: Log in to Azure CLI
          uses: azure/login@v1
          with:
            creds: ${{ secrets.AZURE_CREDENTIALS }}
    
        # List files in the current directory
        - name: List files
          run: ls -la
    
        # Build Docker image
        - name: Build Docker image
          env: 
            LOGIN_SERVER: ${{ vars.LOGIN_SERVER }}
          run: |
            docker buildx build . -t $LOGIN_SERVER/my-app:latest
    
        # Log in to Azure Container Registry
        - name: Log in to Azure Container Registry
          env:
            REGISTRY_NAME: ${{ vars.REGISTRY_NAME }}
          run: |
            az acr login --name $REGISTRY_NAME
    
        # Push Docker image to Azure Container Registry
        - name: Push Docker image
          env:
            LOGIN_SERVER: ${{ vars.LOGIN_SERVER }}
          run: |
            docker push $LOGIN_SERVER/my-app:latest
    ```

1. Once you've updated the workflow file, click on the **Commit changes** option.

   ![](../media/env53.png)

1. Navigate to the **Actions tab (1)** and select the **update docker.yml (2)** action.

   ![](../media/env54.png)

1. You'll be able to see a request for approval as the GitHub username was added in the previous steps. Click on **Review deployments**.

   ![](../media/env55.png)

1. In the **Review pending deployments** pop-up window, select the **action-environment (1)** checkbox and click on **Approve and deploy (2)**.

   ![](../media/env7.png)

1. You'll also be able to see the **wait timer** status, i.e., job1 waited for 2 minutes before starting the execution.

   ![](../media/env56.png)

1. You can also notice the different variables and secret values defined in the Environment. These are fetched and used in the execution task. 

### Summary

In this lab, you learned about setting up a GitHub Environment and verified using a Reviewer account, a Wait timer, Environment variables, and secrets.

