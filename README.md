# Angular 2 in IBM Bluemix

This project deploys a simple Angular 2 app in IBM Bluemix. The Angular 2 uses the [angular-cli](https://github.com/angular/angular-cli) to generate the application artifacts into the **dist** folder. Once generated, these artifacts are deployed to IBM Bluemix and served by the [Cloud Foundry static buildpack](https://github.com/cloudfoundry/staticfile-buildpack).

## Running the app on Bluemix

1. Create a Bluemix Account

    [Sign up][bluemix_signup_url] for Bluemix, or use an existing account.

2. Download and install the [Cloud-foundry CLI][cloud_foundry_url] tool

3. Clone the app to your local environment from your terminal using the following command

  ```
  git clone https://github.com/l2fprod/bluemix-hello-angular2.git
  ```

4. Cd into this newly created directory

5. Install [angular-cli](https://github.com/angular/angular-cli)

  ```
  npm install -g angular-cli
  ```
 > **Note:** this command might need elevated priviledges

6. Initialize angular-cli
  ```
  ng init
  ```
 > **Note:** overwritte all files as requested. (and wait some time at step "Installing packages for tooling via npm")


7. Install the project dependencies

  ```
  npm install
  ```
8. Start project in development mode

 ```
  npm run start
  ```


9. Build the project

  ```
  npm run dist
  ```

  This task defined in [package.json](package.json) compiles the Angular 2 app. In addition it copies the [manifest.yml](manifest.yml) file to the **dist** directory together with the [Staticfile](Staticfile). Those two are needed to deploy the **dist** folder with the [Cloud Foundry static buildpack](https://github.com/cloudfoundry/staticfile-buildpack) making it possible to serve plain HTML, CSS, JavaScript files.

10. Change to the dist directory

  ```
  cd dist
  ```

11. Push the application to Bluemix

  ```
  cf push
  ```

  It will create a new app named *WFG-curation-UI-angular2* with a random route. Watch for the route name in the ```cf push``` output.
 > **Note:** you need to be logged in blumix, use ```cf login``` command.

This project was generated with [angular-cli](https://github.com/angular/angular-cli) version 1.0.0-beta.15.

## Troubleshooting

To troubleshoot your Bluemix app the main useful source of information is the logs. To see them, run:

  ```
  cf logs <application-name> --recent
  ```

---

This project is a sample application created for the purpose of demonstrating the deployment of a Angular 2 app in IBM Bluemix.
The program is provided as-is with no warranties of any kind, express or implied.

[bluemix_signup_url]: https://console.ng.bluemix.net/?cm_mmc=GitHubReadMe-_-BluemixSampleApp-_-Node-_-Workflow
[cloud_foundry_url]: https://github.com/cloudfoundry/cli
