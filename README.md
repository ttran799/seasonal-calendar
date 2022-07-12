<!-- ABOUT THE PROJECT -->
## Seasonal Calendar PowerApp
The Seasonal Calendar Power App is designed to deliver the latest updates of Microsoft products in a visually appealing way for end users. The app uses a playful user interface for this, by always releasing the updates on a monthly basis. It is up to the Admin to decide which articles and products should be displayed in the app, as the data is entered into a SharePoint list. 

![MainImage](https://user-images.githubusercontent.com/106154410/178455421-49438bf4-7f08-4fba-b5eb-9453001a746f.png)

<p align="right">(<a href="#top">back to top</a>)</p>

### Requirements to use the App
* Power Platform license (dedicated license e.g., "Power Apps per User" or included with your Microsoft 365 license)
* SharePoint Team Site

<p align="right">(<a href="#top">back to top</a>)</p>

### The system includes
* Power App Canvas App
* SharePoint List
* Power Automate Flows (To create & update SharePoint List)
* Microsoft Roadmap RSS-Feed 

![JahreszeitenApp](https://user-images.githubusercontent.com/106154410/170679887-aa0ec02e-b6f1-4623-8a6e-af5e31b66561.png)

<!-- GETTING STARTED -->
## Getting Started

To set up the app in your own environment, the files in the Download folder are needed ([Download](https://github.com/ttran799/seasonal-calendar/archive/refs/heads/main.zip)). The folder contains the app and two Power Automate flows. One flow is used to keep the content in SharePoint up to date and the other flow is used to simplify the SharePoint list setup and automatically create the required columns for the list. 

Important: Please note in which environment you want to integrate the system!

### SharePoint setup

A SharePoint page is needed, in which we then create a list. This list contains the posts that will be displayed in the app.

1. Create a SharePoint Site: [Create a site in SharePoint (microsoft.com)](https://docs.microsoft.com/en-us/sharepoint/create-site-collection)

A "Team site" has been created for the app with the name "Seasonal Calendar". If you already have a SharePoint site, you can use it as well.

2. Import the "RoadmapListCreator" flow into your environment. Detailed instructions: Guide_ImportFlow.pdf

After executing the flow, a new list with 9 columns should have been created on the SharePoint page.

Important: 
- When you create a new SharePoint Site, that can take up some time. So you should wait a little bit before you run the Flow. 
- For the column "Summary" the option "Enhanced Rich Text" has to be activated manually. Go to the SharePoint list > Summary > Column Settings > Edit > More Options > "Use enhanced rich...": Yes > Save
- For the column "PublishDate" and "UpdatedDate" the times, as well as the friendly format must NOT be included. PublishDate & UpdatedDate > Include Time = No > Friendly format = No > Save

3. Import of the "RoadmapRSSFlow" flow. The "Guide_ImportFlow" guide can be used again for this. When importing, the connector for RSS must be created, use the same steps as for the SharePoint connector. Now you need to change the necessary actions. You need to make sure to select the correct SharePoint page in the flow. A total of 2 changes must be made. One for the action "Retrieve items" and one for the action "Create item. The second action is included in the action "Loop through RSS feed" > "Check if...". For both changes it is important to select the correct list!

4. Now you can execute the Flow manually, the SharePoint List should be filled with all entries of this year, because you running the Flow for the first time. After that and for the best performance you should edit the flow to always run on the 1st of a month, to set this up: Edit the Flow > Click on the Action "Recurrence" > Show advanced options > Start time: 2022-XX-01T00:00:00Z > Save (XX should be the next upcoming month e.g. If today is 18th June 2022, Start time should be 2022-07-01T00:00:00Z. This flow repeats itself every month to add all entries of the previous month to the list.

Note: The process of inserting all items from the official Roadmap can take more than 5 min, depending on which months you first start the flow. 

Column | Description | 
--- | --- | 
Title | Contains the title of the post |
Product | Affected product |
Summary | Brief description of the change |
PublishDate | Date of publication of the feature or the change |
UpdatedDate | Date of the update for the change or the feature |
URL | Link to the official page for the change |
GA Date | Date for General Availability |
Category | All categories this post has |
GUID | ID to identify the change |

### PowerApp setup
1.	Import the Jahreszeitenkalender.zip file into your environment and change the data source to your own SharePoint Site. Detailed instructions: Guide_ImportApp.pdf

## Customization
### App
After setting up, the app can be customized very easily. Currently, the app is designed so that only the products "Microsoft Teams", "Bookings" and "SharePoint" can be displayed and filtered and also only the articles that are "launched". If other topics are more relevant to you: Go to the component "App" in the tree view > Choose OnStart as the property > And add the technology that you want to display in the Collection "Technologies" (Important: You need to put in the full name of the Technology e.g. "Microsoft Teams" instead of Teams). To make Color changes for each month you can also do that in the property "OnStart".

### Articles
In the SharePoint list you can also decide which posts need to be displayed. For irrelevant posts simply remove them from the SharePoint list. And if you want more articles than "launched" ones in the SharePoint list you need to configurate that in the Flow.

## Share the App into Microsoft Teams
1. Share the App: Go to [PowerApps](make.powerapps.com) > Apps > Choose the App > Share > "Everybody" in the organization > Share
2. Share the SharePoint List: Go to your SharePoint List > Click on the gear icon > List Settings > Permissions for this list > Grant Permissions > Add E-Mail of the Team (you can find it in AAD) > Show options > Set permission level to Read > Share
3. If you want to add the App to Microsoft Teams, please follow this [guide](https://docs.microsoft.com/en-us/power-apps/teams/embed-teams-tab).
