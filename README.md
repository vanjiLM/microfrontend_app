# Introduction

Micro frontend(MFE) project for Film.io aoolication. Details regarding the architecture can be found here: [Architecture Document](https://filmio.atlassian.net/wiki/spaces/UXE/pages/1885470721/Filmio+Front+End+Architecture)

# Getting Started

Clone this repo on your local. There is a `packages` folder in the project which consist of available microfrontend needed in the project. Container folder is the one which will be integerating required microfrontends. All others are independent micro frontend in itself.

To run each micro frontend, do the following:

- cd in to each packages folder and do `npm install`
- `npm run start`
- This will start the dev server on your local in a specific port like (http://localhost:<port>/). Open up this url in browser and you should be able to see MFE

To test microfrontends integrated with each other, run the required mfe and container simultaneously on separate terminals and test it on the localhost:<port>

For production build of a mfe do following:

- cd in to each MFE folder and do `npm install`
- `npm run build`
- This will create a dist folder in respective mfe with the transpiled and bundled code for that specific mfe.

# Build and Workflow

Whenever code is pushed to the master branch of this project and this commit contains a change to lets say ‘container’ folder/packages following are commands executed in a virtual machine hosted by azure:

- Triggers a CI build pipeline.
- Change active folder to the container folder
- Install Dependencies
- Create a production build using webpack `npm run build`
- Create a build artifact with the dist folder content
- Create CD release pipeline to upload the artefact to AWS S3 or Azure blob or private VM

This workflow will be triggered with every mfe.
# For Contributions

- Create a fork of this repo on your machine.
- Create a branch on your fork with same name as your Jira ticket ID.
- Commit and push your branch on your fork.
- Create a PR from your fork to master of this repo.
- Someone from Film.io team will review your PR and will merge it in master.

