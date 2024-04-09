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
    │   ├── src                     # 
    |   │   ├── lib                 # 
    |   |   |   └── assets          # Extra visual elements
    │   |   ├── routes              # 
    |   |   |   └── +page.svelte    # Our webpage
    |   |   |   └── +layout.svelte  # Component that displays the header and footer
    │   |   └── app.html            # Our fallback page
    │   └── static                  # All our visual elements
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



## API Integration


## Deployment

Here I'm going to put info on the server stuff

## Known Issues

Card hover effect refusing to work in directory containing .git but working on a local copy without git despite excact same file structure and contents...