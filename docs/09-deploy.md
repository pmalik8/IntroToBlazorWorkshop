# Deploy to Azure

Blazor Server apps can be deployed to Azure directly from Visual Studio. When deploying Blazor Server apps, we also recommend configuring the Azure SignalR Service to handle connection scale out.

To deploy the Blazor Server app to Azure:

1. Right-click on the BlazorApp1 project and select **Publish**.
1. In the Pick a publish target dialog select **App Service** in the left pane.
1. Select **Azure App Service** > **Create New**.
1. In the drop down select **Create profile**.

    ![Create profile](https://user-images.githubusercontent.com/1874516/67316226-e97fb300-f4bc-11e9-9ec7-da92a219fdb5.png)

1. In the Create new Azure App Service dialog leave the defaults and select **Create**.
1. In the Publish dialog select **Add** in the Dependencies section.

    ![Add dependency](https://user-images.githubusercontent.com/1874516/67317296-c35b1280-f4be-11e9-8005-4bf9d6953e4e.png)

1. In the Add dependency dialog select the **Azure SignalR Server**. Select **Next**.
1. Select the existing Azure SignalR Server from the list. Select **Finish**.
1. Select **Publish**.

Your Blazor Server app is now running on Azure using the Azure SignalR Service! Congrats!
