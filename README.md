
# PlayWright Inizio Kit

This is a starter kit for Playwright framework, which is a powerful Node.js library for automating web browsers.

## Objectives

The main objectives of this starter kit are to:

-   Create a folder hierarchy setup to organize your project files and test data.
-   Set up environment variables to store configuration information such as URLs and credentials.
-   Set up browser drivers for different browsers such as Chromium, Firefox, and WebKit.
-   Provide a module setup that includes a HelperModule to connect with APIs, databases, and JSON/YAML files.
-   Provide a Page Object Boilerplate to create reusable and maintainable test code.

## Project Setup

### Folder Hierarchy Setup

The following is the suggested folder hierarchy for your project:

```
 ├── config/ 
 │ ├──  default.yaml
 │ ├── production.yaml 
 │ └── test.yaml 
 ├── data/ 
 │ ├── test_data.json 
 │ └── test_data.yaml 
 ├── drivers/ 
 │ ├── chromium/ 
 │ ├── firefox/ 
 │ └── webkit/ 
 ├── helpers/ 
 │ ├── api_connector.js 
 │ ├── db_connector.js 
 │ └── json_yaml_connector.js 
 ├── pages/ 
 │ ├── base_page.js 
 │ └── sample_page.js 
 ├── tests/ 
 │ ├── sample_test.js 
 │ └── test_data.js 
 └── playwright.config.js
```
-   The `config` folder contains different configuration files for different environments such as development, test, and production.
-   The `data` folder contains test data in JSON or YAML format.
-   The `drivers` folder contains browser drivers for different browsers.
-   The `helpers` folder contains modules to connect with APIs, databases, and JSON/YAML files.
-   The `pages` folder contains Page Objects that represent web pages or sections of pages.
-   The `tests` folder contains test files that use the Page Objects to perform tests.
-   The `playwright.config.js` file is a configuration file for Playwright that specifies the browser type and other settings.

### Environment Variables Setup

The `config` folder should contain a default configuration file that stores environment variables. You can use the `dotenv` package to load the variables from the file into the `process.env` object. For example:

```js
require('dotenv').config({  path:  './config/default.env'  });  
constBASE_URL  = process.env.BASE_URL;  
const  USERNAME  = process.env.USERNAME;
const  PASSWORD  = process.env.PASSWORD;
```

### Browser Drivers Setup

You can download browser drivers for different browsers from the official Playwright website. Alternatively, you can use the `playwright-browser-luncher` package to automatically download and launch the browsers. For example:

```js
const  { chromium } =  require('playwright'); 
(async  () => {  
  const  browser =  await  chromium.launch({  headless:  false  });  
  const  context =  awaitbrowser.newContext();  
  const  page =  await  context.newPage();  
  awaitpage.goto('https://example.com'); 
})();
```
### Module Setup

The `helpers` folder contains modules that can connect with APIs, databases, and JSON/YAML files. For example, the `api_connector.js` module can use the `axios` package to make HTTP requests to APIs:


```js
const  axios =  require('axios');  
const  BASE_URL  = process.env.BASE_URL;
class  ApiConnector  {  

  static  async  get(endpoint, headers) 
  {  
     const  url =  `${BASE_URL}${endpoint}`;  
     const  response =  await  axios.get(url, { headers });  
     return  response.data; 
   }  
   
   static  async  post(endpoint, data, headers) 
   { 
      const url = `${BASE_URL}${endpoint}`; 
      const response = await axios.post(url,data, { headers }); 
      return response.data; 
```
