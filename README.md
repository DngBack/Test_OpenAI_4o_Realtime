1. Create an .env file and update the following environment variables:

   ```
       AZURE_OPENAI_API_KEY=XXXX
       # replace with your Azure OpenAI API Key

       AZURE_OPENAI_ENDPOINT=wss://xxxx.openai.azure.com/
       # replace with your Azure OpenAI Endpoint

       AZURE_OPENAI_DEPLOYMENT=gpt-4o-realtime-preview
       #Create a deployment for the gpt-4o-realtime-preview model and place the deployment name here. You can name the deployment as per your choice and put the name here.

       AZURE_OPENAI_CHAT_DEPLOYMENT_VERSION=2024-10-01-preview
       #You don't need to change this unless you are willing to try other versions.
   ```

Once you have updated the .env file, please save the changes and you are ready to proceed to the next step.

### Option 1: Run the application locally

1.  Install dependencies:
    Open the terminal and navigate to the src folder of the repository. Then run the following command to install the necesairly Python packages:

        ```pip
        pip install -r requirements.txt
        ```

2.  Run the application: Run the following command to start the application:

    ```chainlit
     chainlit run app.py -w
    ```

3.  Test the application: Open a new terminal and run the following command to test the application:

    ```chainlit
     http://localhost:8000/
    ```

### Option 2: Run the application in a Docker container

1. Navigate to the src folder of the repository

2. Open the file build-docker-image.sh and depending on the architecture of your local machine (linux/arm64 or linux/amd64), uncomment the respective line and comment the other line. Then save the file. In my case I built the image to run it locally on my M1 Mac, so I have uncommented the line for linux/arm64 and commented the line for linux/amd64. If you plan to build the image for a different architecture, you can uncomment the respective line and comment the other line.

3. Run the following command to build the Docker image:

   ```build-docker-image
    ./build-docker-image.sh
   ```

4. Run the following command to run the Docker image:

   ```run-docker-image
    ./run-docker-image.sh
   ```

5. Test the application: Open a new terminal and run the following command to test the application:

   ```chainlit
    http://localhost:8000/
   ```

6. (optional) Push the Docker image to an Azure Container Registry

   If you want to deploy the application to Azure, you can push the Docker image to an Azure Container Registry. To do this, you need to have an Azure Container Registry and the Docker image name and the Azure Container Registry name in the variables.sh file. Once you have updated the variables.sh file, run the following Azure CLI command to connect to your Azure Subscription:

   ```azure
   az login
   ```

   Then run the following command to push the Docker image to the Azure Container Registry:

   ```push-docker-image
   ./push-docker-image.sh
   ```
