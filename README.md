<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## Seasonal Calendar PowerApp
The Seasonal Calendar Power App is designed to deliver the latest updates of Microsoft products in a visually appealing way for end users. The app uses a playful user interface for this, by always releasing the updates on a monthly basis. It is up to the Admin to decide which articles and products should be displayed in the app, as the data is entered into a SharePoint list. 

![image](https://user-images.githubusercontent.com/106154410/170021215-76870ab7-6c44-435e-94e2-0fd394d5f9b0.png)

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

To set up the app in your own environment, it needs the files from the Downloads folder. These must be downloaded first. The folder contains the app and two Power Automate flows. One flow is used to keep the content in SharePoint up to date and the other flow is used to simplify the SharePoint list setup and automatically create the required columns for the list. 

Important: Please note in which environment you want to integrate the system!

### SharePoint setup

A SharePoint page is needed, in which we then create a list. This list contains the posts that will be displayed in the app.

1. Create a SharePoint Site: [Create a site in SharePoint (microsoft.com)](https://docs.microsoft.com/en-us/sharepoint/create-site-collection)

A "Team site" has been created for the app with the name "Seasonal Calendar". If you already have a SharePoint site, you can use it as well.

2. Import the "RoadmapListCreator" flow. Detailed instructions: Guide_ImportFlow.pdf

After executing the flow, a new list with 9 columns should have been created on the SharePoint page.

Important: 
- For the column "Summary" the option "Enhanced Rich Text" has to be activated manually. Go to the SharePoint list > Summary > Column Settings > Edit > More Options > "Use enhanced rich...": Yes > Save
- For the column "PublishDate" and "UpdatedDate" the times, as well as the friendly format must NOT be included. PublishDate & UpdatedDate > Include Time = No > Friendly format = No > Save

3. Import of the "RoadmapRSSFlow" flow. The "Guide_ImportFlow" guide can be used again for this. After activating the flow, the list should be filled with entries. This flow repeats itself every month to add all entries of the previous month to the list. If the flow is executed for the first time, all entries of this year are entered. 

Important: 
- When importing, the connector for RSS must be created, use the same steps as for the SharePoint connector.
- After the import, make sure to select the correct SharePoint page in the flow. A total of 2 changes must be made. One for the action "Retrieve items" and one for the action "Create item. This item is included in the action "Loop through RSS feed" > "Check if...". For both changes it is important to select the correct list!
- During import it can happen that GA Date and PublishDate are not in the correct column. Therefore set PublishDate with the RSS "Feed published on" and GA Date with the variable vGADate.

### PowerApp setup

This is an example of how to list things you need to use the software and how to install them.
* npm
  ```sh
  npm install npm@latest -g
  ```

### Installation

1. Get a free API Key at [https://example.com](https://example.com)
2. Clone the repo
   ```sh
   git clone https://github.com/github_username/repo_name.git
   ```
3. Install NPM packages
   ```sh
   npm install
   ```
4. Enter your API in `config.js`
   ```js
   const API_KEY = 'ENTER YOUR API';
   ```

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3
    - [ ] Nested Feature

See the [open issues](https://github.com/github_username/repo_name/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Your Name - [@twitter_handle](https://twitter.com/twitter_handle) - email@email_client.com

Project Link: [https://github.com/github_username/repo_name](https://github.com/github_username/repo_name)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* []()
* []()
* []()

<p align="right">(<a href="#top">back to top</a>)</p>
