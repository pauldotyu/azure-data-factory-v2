# Copy data from Amazon S3 bucket to Azure Data Lake Gen2

1. Log into [Azure Portal](https://portal.azure.com).

1. Click **+Create a resource** link at top left of the page.

1. In the Azure Marketplace page, click  **Storage** and click on **Storage account** that appears at the top of the **Featured** list.

    ![New](../media/3-copy/1.png)

1. Enter the following and click the **Next: Advanced >** button:
    - Resource Group: Select *adfv2demo-rg*
    - Name: *adfv2demosa* **(NOTE: Must be globally unique, must be lowercase and alphanumeric only)**
    - Location: *East US 2*
    - Performance: *Standard*
    - Account kind: *StorageV2 (general purpose v2)*
    - Replication: *Locally-redundant storage (LRS)*
    - Access tier (default): *Hot*

        ![New data factory](../media/3-copy/2.png)

1. Make sure **Hierarchical namespace** under **DATA LAKE STORAGE GEN2** is set to **Enabled**

    ![The ADLS Gen2 hierarchical namespace accelerates big data analytics workloads and enables file-level access control lists (ACLs).](../media/3-copy/3.png)

1. Click the **Review + create** button, then click the **Create** button.

1. Back in the ADF workspace Overview page, click the **Create pipeline from template** icon.

    ![Create pipeline from template](../media/2-repo/4.png)

1. Click on the template titled **Copy data from Amazon S3 to Azure Data Lake Store**.

    ![Copy data from Amazon S3 to Data Lake Store](../media/3-copy/4.png)

1. Click on the dropdown under **DataSourceConnection** and click **+New**.

    ![Configure source](../media/3-copy/5.png)

1. Enter a connection Name and your Amazon **Access Key ID** and **Secret Access Key**, click **Test connection**, then click the **Finish** button.

    ![Configure Amazon S3 linked service](../media/3-copy/6.png)

1. Click on the dropdown under **DataDestinationConnection** and click **+New**.

    ![Configure source](../media/3-copy/7.png)

1. Enter a connection Name and select the subscription and storage account you created earlier, click **Test connection**, then click the **Finish** button.

    ![Configure Amazon S3 linked service](../media/3-copy/8.png)

1. Click the **Use this template** button.

1. In the **Factory Resources** pane, click on the **DataDestinationStore** and enter a name in the **File Path** text box, and click the **Saave** button. This will be the container in blob storage.

    ![Publish to Git](../media/3-copy/9.png)

1. In the **Factory Resources** pane, click on the **DataSourceStore** and enter your Amazon S3 bucket name in the **File Path** text box, and click the **Saave** button.

    ![Publish to Git](../media/3-copy/10.png)

1. If you've configure a GitHub or Azure DevOps repo, click the **Publish** button, and confirm your changes to be committed and pushed.

    ![Publish to Git](../media/3-copy/11.png)

1. In the Pipeline editor, click **Debug** to execute the copy pipeline.

    ![Publish to Git](../media/3-copy/12.png)

1. Monitor the pipeline execution.

    ![Publish to Git](../media/3-copy/13.png)

1. Verify the data is now in your Azure Data Lake using Azure Storage Explorer

    - Download and install [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer)

    - Open Azure Storage Explorer and click the plug icon to add a new account.

        ![Create new connection](../media/3-copy/14.png)

    - For Azure Environment drowndown, select **Azure** and proceed through sign in prompts.

        ![Create new connection](../media/3-copy/15.png)

    - Browse through your storage account directory structure and find the container that lists your files.

        ![Publish to Git](../media/3-copy/16.png)