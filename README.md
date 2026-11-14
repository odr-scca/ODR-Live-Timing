## ODR Live Timing 

### Website 
 
This repository hosts the website for the ODR live timing site. Every time a new commit is pushed, the /public/ site will redeploy via github actions to the live firebase site: livetiming.html is the file which contains timing info. Live Timing is typically updated within 30 seconds of a recorded time.

Participants should use these links to ODR-SCCA's Live Timing:  
- [Firebase link to the latest ODR-SCCA livetiming.html](https://odr-timing.web.app/livetiming.html)  
- [Github Pages link to the latest ODR-SCCA livetiming.html](https://odr-scca.github.io/ODR-Live-Timing/Website/public/livetiming.html)


### Worker Service

This application runs as a background service on a windows machine. This can be used on the timing computer to connect to the git repo, move the new timing file in, stage, commit, and push changes to git. GitHub will detect these changes and move them onto the firebase server.

#### Installation & Usage

Required before installation: 

.NET 6.0 Hosting Bundle: https://dotnet.microsoft.com/en-us/download/dotnet/6.0  
Git For Windows: https://gitforwindows.org/  
A GitHub Account: https://github.com/  
A GitHub Personal Access Token, with Repo permissions: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#personal-access-tokens-classic  
A clone of this repository  
 

First, download the release from the Releases page in GitHub. Run the .msi installer.
Next, configure the appsettings.json file (located at C:\\Program Files\\Tristan Pressley\\ODR Live Timing Service\\ by default) 

In the app settings file, configure the following selections under "options" 


"SourceFilePath": - this is where the live timing software drops the HTML file 
"DestinationFolderPath": - This is where we are going to drop the file within downloaded repository, including filename
"RepositoryPath": - This is the path to the repo on your machine
"Username": "", - GitHub Username
"PersonalAccessToken": "" - GitHub personal access token 

After changing all of these settings, open task manager, go to services, and find "ODR Live Timing Service". Restart the service. 

The process will now run automatically while the laptop is running. When new live timing files are detected, they will be automatically pushed to GitHub and then to firebase for public access. 
