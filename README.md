![Blazor .NET 8 & Tailwind ](home_screenshot.png)

# Blazor .NET8 & Tailwind 

This repository is a Blazor App SSR in .NET 8 with Tailwind fully configured

You can use this repository as a template.

Once created, just run this command to set the css tailwind generation watching for your changes:


> npx tailwindcss -i wwwroot/css/app.css -o wwwroot/css/app.min.css --watch
* Remember to launch the command inside the BlazorTailwind server folder 


# If you want to create your own Blazor and Tailwind from 0, you can follow these steps.

PostCSS helps in transforming tailwindcss to styling that is relevant to your project. It also helps you remove unnecessary styling which helps in reducing the size of your files.

Start by removing the pre-installed stylesheets in the wwwroot/ folder. Keep the CSS folder because that’s what we’ll use to store our Tailwind input & output CSS files

Next, ensure that you’re still in the BlazorApp Directory then run this command in your terminal:

npm install tailwindcss postcss autoprefixer postcss-cli

Create and configure the PostCSS file

Create a postcss.config.js file in the BlazorApp directory or your root directory and add these configurations:

module.exports = {
    plugins: {
      tailwindcss: {},
      autoprefixer: {},
    }
  }

Run this command in your root directory to generate a Tailwind CSS configuration file:

npx tailwindcss init

You’ll now “tell” Tailwind to watch for files containing utility classes so that the .NET CLI can watch for changes in your project. For our Blazor project, the files that Tailwind needs to track are .html, .cshtml or Razor files. Add the template paths to the content section in your Tailwind config file:

/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./**/*.{razor,html,cshtml}"],
  theme: {
    extend: {},
  },
  plugins: [],
}

Next, create an app.css file in the wwwroot/ folder (within the CSS folder that you did not delete earlier) Add these CSS directives to app.css:

@tailwind base;
@tailwind components;
@tailwind utilities;

Go to your terminal and run the Tailwind CLI to generate the output CSS watch for changes in your project:

npx tailwindcss -i wwwroot/css/app.css -o wwwroot/css/app.min.css --watch

Add a CSS reference to the host file in the Pages directory:

    <link rel="stylesheet" href="/css/app.min.css" />

Finally, run dotnet watch to start adding Tailwind classes to your Blazor project.

You have now successfully created:

- a new Blazor project
- installed and configured Tailwind CSS with Blazor
Up next, we’ll install and configure Flowbite in our Blazor project. We’ll also showcase how to use the Flowbite UI components in a Blazor project through a dropdown component demo.




Install plugins from npm:

npm install -D @tailwindcss/typography
npm install -D @tailwindcss/forms

Then add the plugin to your tailwind.config.js file:

module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('@tailwindcss/typography'),
    // ...
  ],
}
