## Prerequisites

- Node.js installed
- Git installed

## Step 1.
Create a working directory.

Go within local to where you want the directory to be.
```
cd ~/your/directory/path
```

Create the directory.
```
mkdir your-local-directory
```

## Step 2.
Install HubSpot CLI 
```
npm install -g @hubspot/cli@latest 
```

## Step 3.
Configure local dev tools
```
hs init 
```

## Step 4.
Create a [[Theme]] 
```
hs create website-theme my-website-theme 
```
This creates a directory populated with files from the [CMS theme boilerplate](https://github.com/HubSpot/cms-theme-boilerplate).

## Step 5.
Upload theme to HubSpot
```
hs upload my-website-theme my-website-theme 
```
This will upload the theme directory to a my-website-theme folder in your HubSpot account.

