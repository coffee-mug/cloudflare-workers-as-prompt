# Building a Cloudflare Worker with Hono and R2 for Image Upload Tutorial

This tutorial demonstrates how to build a Cloudflare Worker that allows users to upload and view images using Cloudflare R2 for storage. Each section contains a Claude Code prompt that you can copy and send to Claude Code to complete that step of the tutorial.

## Step 1: Project Setup

```
I want to create a Cloudflare Worker project for an image upload application. Let's set up a new project with the following steps:

1. Create a new directory called "image-upload-worker"
2. Initialize a new Cloudflare Worker project, don't use "npm create cloudflare@latest" as this breaks your TTY apparently. Instead, create the needed files for a Worker project.
3. Make sure our project structure is set up correctly for a Worker

Use NPM as the package manager. If you need to install wrangler, please show the command but don't execute it as I'll handle that separately.

Important: stick to only creating the files and folders needed, don't start implementing the API and adding dependencies. This will be done in later prompts. 
```

## Step 2: Adding Dependencies and Configuring R2

```
Now I need to add the necessary dependencies and configure R2 storage. Please:

1. Configure an R2 bucket named "images-bucket" in the wrangler.toml file
2. Add appropriate TypeScript types for our project
3. Update any configuration files as needed

For R2 configuration, we'll need to create a bucket binding that our Worker can access. We'll work locally so please also include necessary configuration to fulfill that requirement.
```

## Step 3: Building the API

```
Let's build the Worker API using Hono. I need functionality to:

1. Upload images to R2 storage
2. Retrieve a list of all uploaded images
3. Get a specific image by its key

First, install Hono in our project. Create the base index.ts file that will contain the application code. 

Then, please create the necessary endpoints:
- POST /upload - for uploading images
- GET /images - to list all images
- GET /images/:key - to get a specific image

Make sure to handle CORS properly to allow browser access, and include appropriate error handling. To do so, use
the included hono cors middleware in "hono/cors"

Do not genrate any front-end for now, it will be tackled in the next prompt. 
```

## Step 4: Building the Frontend

```
Let's create a simple frontend for our application. I need:

1. A basic HTML page with a clean, simple design
2. A form that allows users to select and upload image files
3. A gallery section that displays all uploaded images
4. JavaScript to handle the API communication with our Worker

The HTML file should be placed in the 'public' directory of our Worker project, and all JavaScript should be included directly in the HTML file for simplicity. Add an entry "assets" into the wrangler.toml file, with a sub property "directory" pointing to the assets folder, using a relative path. 


Hono will take care of serving files matching that path automatically, so you don't have to change anything in the hono application's code. 
```

## Step 5: Testing

```
I want to test my application locally. Please:

1. Show me how to configure Wrangler for local development with R2
2. Provide the commands to run the application locally
3. Explain what to look for to verify everything is working correctly

Remember that I'll need to use a local R2 bucket for testing.
```

## Step 6: Deployment

```
I'm ready to deploy my application to Cloudflare. Please:

1. Explain the steps needed to create an actual R2 bucket on Cloudflare
2. Show the commands to deploy my Worker
3. Provide any additional configuration needed for production

Include information about how environment variables or secrets should be handled for the production deployment.
```

Each prompt should be sent to Claude Code one at a time, in sequence. The prompts are designed to be independent but build upon previous steps. If Claude encounters any issues at any step, you may need to clarify or provide additional information.

## Notes for Tutorial Users

- Make sure you have node and npm set up on your machine.
- You'll need a Cloudflare account with Workers and R2 access
- Keep in mind that R2 usage incurs costs, although there is a generous free tier
- The local development experience uses a local R2 replica which won't persist data after shutting down
- For a production application, you would want to add authentication and more robust error handling
- Make sure wrangler is installed. Otherwise you'll be prompted to install it. 