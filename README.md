# landingPage
Repo Containing New Landing Page Frontend 

## Table of Contents
1. [Overview](#overview)
2. [Folder Structure](#folder-structure)
3. [Development Setup](#development-setup)
4. [Key Components](#key-components)
5. [API Integration](#api-integration)

## Overview
This landing page is designed for IdentifAi and built using the Svelte framework to create a fast and interactive user experience.

### Why Svelte?
Svelte uses a compiler driven approach. This means that Svelte shifts much of the heavy lifting from the browser to compile time, resulting in smaller bundle sizes and faster runtime performance.

More specifically, Svelte´s compiler first analyzes the application code and generates optimized JavaScript code design to run faster and use less memory. This framework also provides us with a reactive programming model, where changes to state variables automatically trigger updates to the DOM.

## Folder Structure

    ├── identifai               
    │   ├── src                       # 
    |   │   ├── components            # Where the page elements are stored
    |   |   |   └── Background.svelte # The background particle effect
    |   │   ├── lib                   # 
    │   |   ├── routes                # 
    |   |   |   └── +page.svelte      # Our webpage
    |   |   |   └── +layout.svelte    # Component that displays the header and footer
    │   |   └── app.html              # Our fallback page
    │   └── static                    # All our visual elements
    └── ...


## Development Setup
Suggestion - run this code on VScode with the [Svelte Extension](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) installed

1. Clone the repository
2. Navigate to the project directory.
3. Install dependencies:
     ```bash
     npm install
     ```
4. Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:
    
    ```bash
    npm run dev
    
    # or start the server and open the app in a new browser tab
    npm run dev -- --open
    ```

## Key Components
  ### +page.svelte
 A Svelte component that serves as a primary interface for our application. It is responsible for rendering the main content of the application.
  ### +layout.svelte
  A Svelte component that provides the layout for our application. It includes the header, footer, and main content area. It uses slots to allow other components to insert content into these areas.
  ### app.html
  The main HTML file for our application. It includes the root element where our Svelte application is mounted. It also includes the script tag that loads our compiled Svelte application.

## Deployment

### First server access
SSH into the server
```
ssh root@137.184.14.124
```
Install the NGINX Webserver
```
apt install nginx
```
Install the Python required libraries

```
apt install python3-fastapi
```
Navigate to the respoistory containing the .git
```
cd landingPage/
```
Pull the github code into the server
```
git pull origin
```
Run the code!
```
npm run dev -- --host
```

## Known Issues

Card hover effect refusing to work in directory containing .git but working on a local copy without git despite excact same file structure and contents...