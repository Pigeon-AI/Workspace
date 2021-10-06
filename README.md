# Visual Studio Code Development Workspace

This repo uses git submodules, Docker, and VSCode remote development containers to get development up and running quickly on any computer.

## Install Directions

1. Install Docker and make sure it's running.
2. Install Visual Studio Code, and install the 'Remote - Containers' extension.
3. Clone the repository into a named container volume in VSCode.
   * Open the VSCode command prompt (&#8984;-Shift-P on Macs)
   * Type 'clone'
   * Select the correct popup. ![Image of VSCode Window](https://i.imgur.com/SGCBPsL.png)
   * Provide this repository git address: `https://github.com/Pigeon-AI/Workspace.git`
   * Provide any name you'd like for the volume, I used 'Pigeon-AI'
   * Provide any name you'd like for the folder, I used 'Workspace'
   * **Do not** click 'Open Workspace', open a terminal instead, it should be in the /workspaces/Workspace/ folder.
   * Clone the two repositories
     - `git clone https://github.com/Pigeon-AI/API.git`
     - `git clone https://github.com/Pigeon-AI/Extension.git`
   * Click on the workspace file in the file selector and now click 'Open Workspace'.
   * You now have the workspace setup with all dependencies!
5. (Optional) If you're going to be building / working on the extension install all yarn dependencies:
   - Make sure you're in the Extension folder
   - yarn install
6. (Optional) If you're going to be running the API locally you'll want to install the https certificates:
   * On your local machine install the certificate and export it to an easily accessible file.
     - `dotnet dev-certs https --trust -ep ~/Downloads/aspnetcore.pfx -p test`
   * Drag the file into an easily accessible location in the VSCode container, like the API folder
   * Inside the VSCode container terminal import the certificate
     - `dotnet dev-certs https --clean --import /workspaces/Workspace/API/aspnetcore.pfx -p test`
   * Delete the certificate file both from your machine, and in the VSCode container.

## Build Extension Directions

1. Open a terminal in the Extension Directory in your VSCode container.
2. `yarn build`
3. Right click the build folder in VSCode that was created and click 'Download' to somewhere on your local computer.
4. Open Chrome > Extensions.
5. Enable Developer Mode
6. Click 'Load Unpacked'
7. Select the build folder you downloaded.

## Build API Directions

1. Open a terminal in the API Directory in your VSCode container.
2. `dotnet run --project src/`


