# HOW TO SETUP A QUASAR-VUE CAPACITOR ANDROID PROJECT 
![[logos.png]]

## Introduction

There are a number of steps you need to perform to properly scaffold and configure your Quasar-Capacitor project for creating Android apps using Vue.js.

This guide assumes:
- You are running VS Code (though in general this should work with other IDEs)
- You are familiar with Vue.js, as it is a foundation for Quasar and an initial Vue.js project is scaffolded when you initialize Quasar

## About This Guide

I have attempted to show Information that has been directly gleaned from the internet and then "cut-n-pasted" incorporated into this guide between sets of lines and "Per research".

This guide is intended for someone who is starting out on their journey (like me). Experienced developers will likely find most of the information, well, *superfluous*.

> [!faq]-  Disclaimer & Rant
> ## Disclaimer
> 
> There are very probably egregious errors, omissions, and mistakes in this guide. If you find them, blame a couple things:
> -The paucity of existing documentation on the Quasar and Capacitor websites (as of Feb 2025). 
> --The Quasar web site doesn't have much to say about Capacitor.  
> --And the Capacitor website doesn't have much to say about Quasar.  
> If there was actual documentation on how to properly integrate these two frameworks, I would not have found putting this guide together worth the effort in the first place. 
> -Oh, and also blame the fact there is so much to learn about Quasar!...and I'm just learning.
> 
> The following image pretty much captures the experience of trying to get a clean install of a Quasar-Capacitor-Android project: What a headache.
> 
> ![[headcrusher.png]]
> 


# QUASAR IS AN AWESOME FRAMEWORK!

Quasar and Capacitor are truly wonderful, but I've found it a bit difficult to get them to behave, so hence this guide. At the end of all this you should behold the following desktop configuration!

![[desktop.png]]

 > [!info]- Quick links to Quasar and Why Quasar?
 >  Here's a few links to relevant information
 >  
 >   https://capacitorjs.com/
 >   
 >   https://quasar.dev/
 >   
 >   https://vuejs.org/
 >
 >Note of Why Quasar?
 >Take the notes below with a grain-of-salt...some of it is pure opinion.  Do your own reasearch!
 >
 > There are other frameworks out there besides Quasar that will help develop cross platform apps with one code base to target multiple platforms, such as Flutter, React Native, and Xamarin, and Ionic. 
 > 	
 > 	Flutter is a Google thing...and Google simply abandons products without a second thought. I've been burned so many times relying on a Google platform or framework that simply disappeared, that I would never adopt anything they make unless forced too by their market monopoly power, such as Google Maps.
 >	
 >	React Native...well you have to learn React. But it supposedly renders native UI components instead of using WebView[1](https://www.jetbrains.com/help/kotlin-multiplatform-dev/cross-platform-frameworks.html)[2](https://appinventiv.com/blog/cross-platform-app-frameworks/). This results in apps that are supposedly indistinguishable from those built using native languages like Objective-C or Java. 
 >	
 >	.Xamarin... this is a Microsoft framework, requires C# and .NET. Yuck. I'd probably have to buy a windows machine. More Yuck. But, It compiles directly to native code, avoiding the use of WebView.
 > 	
 >	Ionic looks pretty good, but it's just a javascript/typescript thing?  I don't really know, but as of 2025 it's more popular than Quasar, so that does say something.
 >	
 >	Quasar - so far, given that I'm primarily developing with Vue.js, I haven't found a better framework to develop in.
 > 	
 > Some more notes Per research further discussion:
 > 	
 > Ionic and Quasar are both popular frameworks for cross-platform app development, but they have some key differences:
>	
>	Performance and Rendering
>	
> 	Ionic relies on WebView for app rendering, which can sometimes result in performance issues[1](https://stackshare.io/stackups/ionic-vs-quasar-framework). Quasar, on the other hand, takes advantage of platform-specific features, potentially offering better performance and a more native feel[1](https://stackshare.io/stackups/ionic-vs-quasar-framework).
>
>  **Challenges of WebView-Based Frameworks**
> 
> 1. **Performance Limitations**: WebViews may not match the speed or responsiveness of fully native apps due to additional rendering layers[2](https://stackoverflow.com/questions/15024400/is-it-useful-using-webview-whole-layout-in-native-android-app)[4](https://felgo.com/mobile-app-framework-comparison).
>     
> 2. **Device Compatibility Issues**: Variations in WebView implementations across operating systems can lead to inconsistent behavior[4](https://felgo.com/mobile-app-framework-comparison).
>     
> 3. **Limited Access to Native Features**: While plugins can bridge some gaps, certain advanced device functionalities may not be accessible[2](https://stackoverflow.com/questions/15024400/is-it-useful-using-webview-whole-layout-in-native-android-app)[6](https://stackoverflow.com/questions/38157790/are-ios-android-apps-with-webview-only-considered-hybrid-or-web-apps).
>     
> 4. **User Experience Concerns**: Apps relying heavily on WebViews may feel less fluid compared to native applications[7](https://www.mobiloud.com/blog/native-app-vs-webview-app).
>
> 	 Platform Support
> 	
> 	While Ionic primarily focuses on hybrid mobile applications, Quasar targets a broader range of platforms including mobile (iOS, Android) using Capacitor, desktop (Windows, Mac, Linux) using Electron, and web applications including SPA and SSR [1](https://stackshare.io/stackups/ionic-vs-quasar-framework)[2](https://www.bacancytechnology.com/blog/quasar-framework-full-frontend-stack).
> 	
> 	 UI Components and Design
> 	
> 	Ionic offers pre-built UI components following Material Design and Apple's Human Interface Guidelines[1](https://stackshare.io/stackups/ionic-vs-quasar-framework). (Ionic seems to have an Apple bias)
> 	 Quasar provides a more extensive set of components and styling options, offering both Material Design and iOS-style components[1](https://stackshare.io/stackups/ionic-vs-quasar-framework)[2](https://www.bacancytechnology.com/blog/quasar-framework-full-frontend-stack).
> 	
> 	 Framework Base
> 	
> 	Ionic can be used with various JavaScript frameworks, while ==Quasar is built specifically on Vue.js,== offering seamless integration with Vue's ecosystem[1](https://stackshare.io/stackups/ionic-vs-quasar-framework)[3](https://www.linkedin.com/pulse/what-quasar-framework-why-leading-among-other-javascript-maitri-patel-qu1ef).
> 	
> 	Development Experience
> 	
> 	Quasar is often praised for its comprehensive toolset, which includes a wide range of UI components, layout elements, and helpers[2](https://www.bacancytechnology.com/blog/quasar-framework-full-frontend-stack). It also offers features like code splitting, lazy loading, and server-side rendering out of the box[2](https://www.bacancytechnology.com/blog/quasar-framework-full-frontend-stack).
> 	
> 	 Community and Ecosystem
> 	
> 	Ionic has a larger, more established community with extensive documentation and a broad range of plugins[1](https://stackshare.io/stackups/ionic-vs-quasar-framework). 
> 	
> 	Quasar, while newer, has a growing community and offers a collection of ready-to-use plugins and integrations[1](https://stackshare.io/stackups/ionic-vs-quasar-framework)[3](https://www.linkedin.com/pulse/what-quasar-framework-why-leading-among-other-javascript-maitri-patel-qu1ef).
> 	
> 	 Performance Optimization
> 	
> 	Quasar emphasizes performance with built-in features like code minification, source mapping, and tree shaking[2](https://www.bacancytechnology.com/blog/quasar-framework-full-frontend-stack).
> 	
> 	 Customization and Theming
> 	
> 	Quasar offers more extensive theming capabilities, including support for right-to-left (RTL) languages[2](https://www.bacancytechnology.com/blog/quasar-framework-full-frontend-stack).
> 	
> 	In summary, while various frameworks have their strengths, Quasar seems to offer more flexibility in terms of platform support and potentially better performance, especially for Vue.js developers. However, Ionic's larger community and ecosystem might be advantageous for some projects.

## Guide Structure

This guide is divided into four major parts:

1. **Prerequisites for a Quasar / Vue project**  
   Setting up your development environment 

2. **Project Planning**  
   What you need to consider before starting 

3. **Project Setup Steps**  
   Detailed configuration steps with thorough explanations 

4. **Launching Your Android Application in Dev**  
   Getting your development environment running 

Oh, and some credits are at the end...

# PART 1: Prerequisites for a Quasar Project
 
## Prerequisites Checks
There are 3 steps:
	-have Node, nvm and npm installed
	-verify Android Studio install
	-set environment variables


### Part 1 - Step 1. Check Node.js, npm, and nvm versions:
First, let's verify the development environment

==**Important DO NOT IGNORE:**  ==
As of Feb 2025, default Quasar & Capacitor (v6) required Node v18.
This will probably change, hence why having node version manager (nvm) is essential.

Terminal commands:

```bash
node --version  # Should be >=18.0.0
npm --version   # Should be >=6.13.4
nvm --version   # Check if nvm is installed
```

If nvm is not installed:
```bash
# For macOS using brew
brew install nvm
```

After installation, add these lines to your ~/.zshrc or ~/.bash_profile:
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"
[ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"
```

Reload your terminal configuration:
```bash
source ~/.zshrc  # or source ~/.bash_profile
```

Verify nvm installation:
```bash
nvm --version
```

If Node.js version is not 18:
```bash
# Install Node.js 18
nvm install 18

# Use Node.js 18
nvm use 18

# Verify the version
node --version  # Should show v18.x.x (for Capacitor v6)
```

To use a specific version directly, use the terminal command:
```bash
nvm use <version>
```


> [!info]- Per research NPM - NPX:
> ***********
> npm and npx are both tools used in Node.js development, but they serve different purposes:
> **npm (Node Package Manager)**
> - Used for installing and managing packages in Node.js projects
> - Primarily handles package installation, either locally or globally
> - Manages dependencies listed in the package.json file
> - Requires packages to be installed before they can be used
> - Usage: `npm install <package>`
>
> **npx (Node Package Execute)**
> - Executes Node.js packages without requiring installation
> - Allows running packages directly from the npm registry
> - Ideal for one-time or infrequent package usage18
> - Can run different versions of packages without conflicts
> - Usage: `npx <package>`
> ***********
> 
> I have more notes in some following sections on npx

> [!info]- Per research: Node Modules
> ************
> The node_modules folder plays a crucial role in your Quasar and Capacitor project, as it does in most Node.js-based applications:
> 
> **Dependency Storage:**  
> node_modules is where all the external libraries and packages that your project depends on are stored15. This includes Quasar, Capacitor, and any other packages you've installed using npm or yarn.
> 
> **Local Package Access:**  
> When you import a package in your code, Node.js looks for it in the node_modules folder1. This allows your application to use these dependencies without needing to specify their full path.
> 
> **Project-Specific Dependencies:**  
> Each project has its own node_modules folder, ensuring that different projects can use different versions of the same package without conflicts.
> 
> **Automatic Management:**  
> When you run npm install or yarn install, the package manager reads your package.json file and downloads all the required dependencies into the node_modules folder.
> 
> **Exclusion from Version Control:**  
> The node_modules folder is typically not included in version control systems like Git due to its large size35. Instead, developers share the package.json file, which lists all the dependencies.
> 
> **Recreating Dependencies:**  
> Other developers can recreate the node_modules folder on their machines by running npm install or yarn install, using the package.json as a reference.
> 
> For Quasar and Capacitor specifically:
> - These frameworks, along with their dependencies, are stored in node_modules when you set up your project
> - When you add Capacitor plugins to your Quasar project, they are installed into the node_modules folder
> - Remember, if you're having issues with missing modules after cloning a repository or switching branches, try deleting the node_modules folder and package-lock.json file, then running npm install again to ensure all dependencies are correctly installed4
> ************



### Part 1 - Step 2. Verify Android Studio installation:

Open Android Studio and verify the following:

Go to Tools > SDK Manager
Under "SDK Platforms" ensure you have:
- Android 14.0 (API 34) or latest stable
- Android 13.0 (API 33)

Under "SDK Tools" verify you have:
- Android SDK Build-Tools
- Android SDK Command-line Tools
- Android Emulator
- Android SDK Platform-Tools

### Part 1 - Step 3. Set up environment variables

Add to ~/.zshrc or ~/.bash_profile:
```bash
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

> [!info]- What environment variables do
> **What These Lines Do:**
> 
> `export ANDROID_HOME=$HOME/Library/Android/sdk`:
> - Sets the ANDROID_HOME environment variable to the directory where the Android SDK is installed
> - The ANDROID_HOME variable is used by many Android tools to locate the SDK
> - Tools like Gradle, Android Studio, and command-line utilities rely on this variable
> 
> `export PATH=$PATH:$ANDROID_HOME/tools`:
> - Appends the tools directory inside the Android SDK to your system's PATH
> - Allows you to run commands like android from any location without typing the full path
> 
> `export PATH=$PATH:$ANDROID_HOME/platform-tools`:
> - Appends the platform-tools directory to your system's PATH
> - Contains essential utilities like adb (Android Debug Bridge) and fastboot
> 
> **Why This Is Important:**
> - Makes Android development tools easily accessible from the command line
> - Eliminates need to type full paths to tools
> - Essential for tasks like building apps, managing emulators, or debugging devices
> 
> **How It Works in Practice:**  
> After adding these lines to your .zshrc, you can:
> - Use commands like adb devices or emulator -avd <avd_name> directly
> - Run Gradle builds or other tasks that depend on the Android SDK

To apply these changes immediately after editing .zshrc, run:
```bash
source ~/.zshrc
```
This will reload your shell configuration and make the environment variables available in your current terminal session.

# PART 2: Project Planning
 
Before you begin scaffolding Quasar, think carefully about the following names: ^90b947
- Directory & Name
- Product Name
- App ID
- Capacitor AppName

 > [!info]- Notes on naming
>  ## Part 2 - Note 1. Directory & Name
> 
> Plan the naming of your project name-directory-folder.
> - You will be using cd a lot, so don't get too carried away: keep it simple
> - This will also be the "name" in your root package.json file
> - This is typically lowercase, no spaces
> - Used for the project directory and npm package name
> - Best practice: Use kebab-case (e.g., "my-map-app") or single words
> 
> ## Part 2 - Note 2. Product Name
> 
> Product Name ("productName" in root package.json):
> - This is the user-friendly display name
> - Can include spaces and proper capitalization
> - This often appears in the app launcher, title bar, etc.
> 
> ## Part 2 - Note 3. App ID
> 
> Capacitor App ID (appId in capacitor.config.json):
> - Should follow reverse domain name notation
> - Format: com.company.appname
> - In my case I used a GitHub Pages domain: "com.abcdefg2.org"
> - Best practice: Use a domain you control
> - This is important for app stores and must be unique
> - Even if you are creating an Android app, you could still launch a test as a spa
> 
> ## Part 2 - Note 4 Capacitor AppName
> 
> Capacitor App Name (appName in capacitor.config.json):
> - Usually matches the productName in package.json
> - This is what shows under the app icon
> 


# PART 3: Quasar Project Setup Steps

This section provides detailed instructions for setting up your Quasar project with Capacitor for Android development. Follow these steps in order: ^978f19

## Part 3 Overview

###  A - Install Quasar CLI
Installation and configuration of the Quasar Command Line Interface [[#Part 3A - Install Quasar CLI|link]]

###  B. Scaffold Quasar / Vue
Creating the base Quasar & Vue project structure [[#Part 3B - Scaffold Quasar / Vue|link]]

### C. Add Capacitor to Quasar
Integrating Capacitor framework with your Quasar project [[#Part 3C - Add Capacitor to Quasar|link]]

### D. Add Capacitor/android to project
Setting up the Android platform configuration [[#Part 3D - Add Capacitor/android to project|link]]

### E. Create /dist directory
Preparing the distribution directory for your application [[#Part 3E - Create Dist/Spa Directory|link]]

### F. Sync the project
Synchronizing Quasar and Capacitor configurations [[#Part 3F - Sync Your Project|link]]

### G. Install capacitor plugins 
Adding and configuring Capacitor plugins [[#Part 3G - Install Capacitor Plugins|link]]

Each step will be covered in detail in its own section. Follow the steps sequentially to ensure proper setup of your development environment.


### Part 3A - Install Quasar CLI

In your project directory, first check the install of the Quasar CLI: ^1c3ed6

```bash
quasar --version
```

The above command will return the CLI version if installed, something like:
```
@quasar/cli 2.4.1
```

Run the Quasar CLI install command if not already installed:
```bash
npm i -g @quasar/cli
```

Note also that you can run the following command:
```bash
quasar info
```

This will show a complete report of your Quasar project (if the Quasar framework project has been scaffolded).

### Part 3B - Scaffold Quasar / Vue
 
![[quasar.png]] 

To initialize and scaffold the Quasar and Vue.js project: 
-Create Quasar project
-Install and verify
-Test initial build

#### P3B Step 1: Create new Quasar project

Run this command:
```bash
npm init quasar@latest
```

Or run this command:
```bash
npm create quasar
```

As of Feb 2025, I can't determine definitively which of the above commands is better.   Either command will then prompt the same set of selection options: see note below. 

> [!faq]- If npm hangs
> The command `"npm init quasar@latest"` will often hang on this last step:
> ```
> ✔ Install project dependencies? (recommended) › Yes, use npm
> ```
> 
> It may fail with this message:
> ```
> npm error code UNABLE_TO_GET_ISSUER_CERT_LOCALLY
> npm error errno UNABLE_TO_GET_ISSUER_CERT_LOCALLY
> npm error request to https://registry.npmjs.org/@eslint%2fjs failed, reason: unable to get local issuer certificate
> ```
> 
 > When this happens, you'll see:
> ```
> Quasar • ⚠️  Could not auto install dependencies. Probably a temporary npm registry issue?
> Quasar • Initialized Git repository 🚀
>
>To get started:
 > `cd yourprojectfolder`
 > yarn #or:` `npm install`
>  yarn lint --fix # or: `npm run lint -- --fix`
 > quasar dev # or: yarn quasar dev # or: `npx quasar dev`
>  ```
>Documentation can be found at: https://quasar.dev
>
>This is why you often need to run `npm install` and `npx cap sync`. Note there doesn't seem to be any harm in running these two commands multiple times.


> [!info]- detailed list of selection options
> - ? What would you like to build?
>  - Select: **App with Quasar CLI, let's go! - spa/pwa/ssr/bex/electron/capacitor/cordova**
>- Project folder: `<your project folder name>`
>- Select: **Quasar v2 (Vue 3) latest and greatest - recommended**
>- Choose: **Javascript** or TypeScript (Javascript is easier for beginners)
>- Select: **Quasar App CLI with Vite 6 (v2) - recommended** (Important!)
>- Package name: `<whatever you need-could be project folder name>`
>- Project product name: `Must start with letter if building mobile apps` (e.g., My Quasar App)
>- Project description: A Quasar test
>- Select: **Composition API with `<script setup>`**
>- Pick your CSS preprocessor: **Sass with SCSS syntax**
>- Check the features needed for your project:
  >- Vue Router (Yes)
  >- Pinia (Yes)
 > - ESLint (Yes)
  >- Install dependencies (Yes)
>
#### P3B Step 2: Install & Verify

Change directories into the project root:
```bash
cd <your project folder>
```

Then run:
```bash
npm install
```

Verify the terminal output resulting from the install

> [!info]- What npm install does
>Running "npm install" performs the following actions:
>
>**Installs Dependencies:**
>- Reads the package.json file to identify all dependencies
>- Downloads dependencies from npm registry
>- Installs them into the node_modules folder
>
>**Creates or Updates package-lock.json:**
>- Uses existing package-lock.json if it exists
>- Generates new one if it doesn't exist
>- Locks dependency versions for consistency

Also run in your project root:
```bash
quasar info
```
- Check Quasar installation
- Verify Vite is listed as the build tool
 > [!info]- quasar info terminal output
 > *following is when my project was pretty much fully scaffoled/configured*
 > 
> Operating System - Darwin(23.5.0) - darwin/arm64
> ==NodeJs - 18.20.6==
> 
> Global packages
>   ==NPM - 10.8.2==
>   yarn - Not installed
>   pnpm - Not installed
>   bun - Not installed
>  ==@quasar/cli - 2.4.1==
>   @quasar/icongenie - Not installed
>   cordova - Not installed
> 
> Important local packages
>   ==quasar - 2.17.7== -- Build high-performance VueJS user interfaces (SPA, PWA, SSR, Mobile and Desktop) in record time
>   ==@quasar/app-vite - 2.1.0==-- Quasar Framework App CLI with Vite
>   @quasar/extras - 1.16.17 -- Quasar Framework fonts, icons and animations
>   eslint-plugin-quasar - Not installed
>   ==vue - 3.5.13== -- The progressive JavaScript framework for building modern web UI.
>   vue-router - 4.5.0
>   pinia - 3.0.1 -- Intuitive, type safe and flexible Store for Vue
>   ==vite - 6.1.0== -- Native-ESM powered web dev build tool
>   vite-plugin-checker - Not installed
>   eslint - 9.20.1 -- An AST-based pattern checker for JavaScript.
>   esbuild - 0.24.2 -- An extremely fast JavaScript and CSS bundler and minifier.
>   typescript - Not installed
>   workbox-build - Not installed
>   register-service-worker - Not installed
>   electron - Not installed
>   @electron/packager - Not installed
>   electron-builder - Not installed
>   ==@capacitor/core - 6.0.0==-- Capacitor: Cross-platform apps with JavaScript and the web
>   ==@capacitor/cli - 6.2.0==-- Capacitor: Cross-platform apps with JavaScript and the web
>   ==@capacitor/android - 6.0.0==-- Capacitor: Cross-platform apps with JavaScript and the web
>   @capacitor/ios - Not installed
> 
> Quasar App Extensions
>   *None installed*
> 
> Networking
>   Host - abcdefgh-MacBook-Air.local
>   en0 - 10.0.0.125


#### P3B Step 3: Test initial build
You will now want to make sure Quasar (and Vue) are working as a plain web app.

```bash
npm run dev    # Should open development server
```

> [!info]- Quasar Project Structure
>After running `npm init quasar@latest` your project structure should look something like this:
>
>```
>your-project/
>├── .quasar                  <-quasar
>├── node_modules
>├── src/                     <- src/ folder Vue project.
>│   ├── assets
>│   ├── components/
>│   │   └── EssentialLink.vue
>│   ├── css
>│   ├──layouts/
>│   │   └── MainLayout.vue
>│   ├── pages/
>│   │   ├── IndexPage.vue
>│   │   └── ErrorNotFound.vue           
>│   ├── router/
>│   │   ├── index.js
>│   │   └── routes.js                      
>│   └── App.vue
>├── index.html
>├── package-lock.json
>├── package.json             <- Pay close attention to dependency versions
>└── quasar.config.js         <-quasar
>```
>The above `/src` folder should look familiar to a Vue.js developer.
>The package.json in the project `root` will have a dependency list similar to the following:
>
>```json
>{
  >"dependencies": {
>    "@quasar/extras": "^1.16.4",   <-quasar
 >   "axios": "^1.2.1",
 >   "pinia": "^3.0.1",
 >   "quasar": "^2.16.0",           <-quasar
 >   "vue": "^3.4.18",
>    "vue-router": "^4.0.0"
>  },
> "devDependencies": {
>   "@eslint/js": "^9.14.0",
>    "@quasar/app-vite": "^2.1.0",  <-quasar
>    "autoprefixer": "^10.4.2",
>    "eslint": "^9.14.0",
>    "eslint-plugin-vue": "^9.30.0",
>    "globals": "^15.12.0",
>    "postcss": "^8.4.14",
>    "vite-plugin-checker": "^0.8.0"
>  }
>}
>```
>
>Note there are no Capacitor-related elements yet.

#### Part 3B Summary of scaffolding Quasar

So, in summary to Part 3B, to initially scaffold the Quasar project, run these 3 commands:
```bash
npm i -g @quasar/cli
npm init quasar@latest
npm install
```

The above 3 commands will:
1. Allow you to run Quasar CLI commands
2. Create an initially scaffolded Quasar-Vue project


### Part 3C - Add Capacitor to Quasar
There are a couple steps to install capacitor to a Quasar project. 
-Add capacitor structures to project using Quasar command
-Add capacitor config to project `root` using npm commands
-Verify installation

#### P3C - Step 1: Add Capacitor to Quasar

Run the following ==*Quasar command*== in your project root folder:

```bash
quasar mode add capacitor
```

The above ==*Quasar command*== will prompt for:

> What is the Capacitor app id? (org.capacitor.quasar.app)

The app id is reverse domain name notation (ref project planning notes)

The folder `/src-capcitor` will then be created in your project and the app id will go into the `capacitor.config.json` file.

The newly created `src-capacitor` structure will also hold the android structures in subsequent steps.

##### P3C Step 1 Notes
I recommend you review each of the notes below after running `quasar mode add capacitor`.


> [!warning]- A Versioning Rant: Quasar defaults v6
> Running `quasar mode add capacitor` will probably ==default in older versions of capacitor (**v6**)==, as shown in the `package.json` in `/src-capacitor` folder (as of Feb 2025).
> 
> Research indicates the Quasar team have the command `quasar mode add capacitor` default in a supposedly *more stable* versions of capacitor at v6 (but Capacitor plugins, as of Feb 2025, are at v7)
>  
> 
> The version is crucial!
> Subsequent steps to `install @capacitor/android` and other capacitor plugins can run into version issues, because version 7 of `@capacitor/android` will default in, which will conflict with @capacitor/core at v6.
> 
> You may see an error msg such as this:
> 
> ```
> [warn] @capacitor/core@6.2.0 version doesn't match @capacitor/android@7.0.1 version.
> Consider updating to a matching version, e.g. w/ npm install @capacitor/core@7.0.1
> ```
> 
> Attempts to upgrade capacitor/core might drag you down a rabbit hole of chained updates to your entire project, including Node.js.
> 
> It appears that (as of Feb 2025) Capacitor v6 requires Node v18. 
> 
> -But Capacitor v7 requires Node v20. 
> 
> -But Node v20 doesn't apparently work with the Quasar version that is defaulted in my `npm create quasar.`
> 
> So I recommend avoiding to attempts to upgrade individually.  And note: I was never able to land a clean working v7 Capacitor into my Quasar project.  Again: there seems to be no comprehensive versioning guide to install a Node-Vue-Quasar-Capacitor-Android-plugin stack. 
> 
> here's some links to other notes ranting about version dependencies:
> [[#P3D Step 1 Notes]]
> [[#P3G Step 1 Note 1 Versioning Challenges read]]

> [!info]- Notes on Quasar Install vs NPM install
> Running command `quasar mode add capacitor` in project root does of course negate the need to run specific NPM commands in a `/src-capacitor` folder:
> 
> - `npm install @capacitor/core`
> - and
> - `npm install @capacitor/cli`
> 
> Per research:
> *************
> Running `"quasar mode add capacitor"` does more than just installing the Capacitor core package.
> Here's why it's important:
> - It sets up the Capacitor integration within your Quasar project structure.
> - It creates a dedicated `"/src-capacitor"` folder in your Quasar project, which contains the necessary configuration files for Capacitor.
> - It automatically adds platform-specific folders (ios and android) to your project root when you add those platforms.
> - It configures your Quasar project to work seamlessly with Capacitor, including setting up build processes and development scripts.
> - It ensures compatibility between Quasar and Capacitor versions, reducing potential conflicts.
> 
> Simply running `"npm install @capacitor/core"` (in project root) would only install the core package without integrating it properly into your Quasar project structure or setting up the necessary configurations. The `"quasar mode add capacitor"` command provides a more comprehensive and streamlined setup for using Capacitor with Quasar
> *************
> 
> Rant Alert: But, why running "quasar mode add capacitor" also does not update the `package.json` and node_mooules in the Quasar project root is simply inexplicable and exasperating.  It should, as this just creates extra steps and opportunities for error and confusion.


> [!warning]- Warning Notes on npx cap init
> If your floundering around the internet attempting to figure out how to land a clean install of Quasar-Capacitor-Android, you will probably come across the cmnd:
> 
> ```bash
> npx cap init
> ```
> 
> This command `npx cap init `will create a completely new scaffold of your project right on-top of everything you've done with `"quasar mode add capacitor"`. Thus you will either duplicate files and directories, or over-write files and directories...either way it's kind-of-mess. If using quasar to install capacitor, I recommend avoiding also using "npx cap init".


 > [!info]- Recommend Examine Capacitor Project Structure & package.json
>
> At the end of scaffolding capacitor when using the Quasar command `quasar mode add capacitor`, the project structure should look something like this:
>
>```
>your-project/
>├── .quasar
>├── node_modules
>├── src/
>├── src-capacitor/        <- new folder created
>│   ├── node_modules       <- Yet another set of node_modules!
>│   ├── www
>│   ├── capacitor.config.json
>│   ├── package-lock.json
>│   └── package.json      <- Yet another package.json file!
>├── index.html
>├── package-lock.json
>├── package.json
>└── quasar.config.js
>```
>
>The `package.json` file under `/src-capactor` folder should look something like this:
>
>```json
>{
  >"name": "gmap9",
  >"version": "0.0.1",
  >"description": "A Quasar Google Map test",
  >"author": "abcdefg2 <abcdefg2@icloud.com>",
  >"private": true,
  >"dependencies": {
>    "@capacitor/app": "^6.0.0",     <- v6!!!
>    "@capacitor/cli": "^6.0.0",     <- v6!!!
 >   "@capacitor/core": "^6.0.0".    <- v6!!!
 > }
>}
>```
>
>***Special Note: Notice above that Quasar defaulted in v6 capacitor!!!***

> [!info]- Notes regarding capacitor app, core and cli
> Each of the files perform different function (duh)
> 
> **@capacitor/app**
>This is a specific Capacitor plugin that provides functionality related to the app itself.
> It offers methods for handling app-level events and information, such as:
>   - Detecting when the app is put into the background or brought to the foreground  
>   - Accessing app information like build and version numbers 
>   - Handling deep links  
>   - Managing app exit events   
>  It's an optional plugin that you can add to your project for additional app-specific functionality.
>NOTE: @capacitor/app **does ==not== need** a separate install step in the `root` package.json.
>
> **@capacitor/core**:
> This is the main package that provides the core functionality and APIs for Capacitor.
> It contains the JavaScript runtime that allows web apps to interact with native platform features.
> It's used in your web application code to access Capacitor's APIs and plugins. 
> It provides a consistent API layer that works across all platforms (iOS, Android, and web).
>NOTE: @capacitor/core ** does need ** a separate step to install in the `root` package.json
>
>**@capacitor/cli**
> The @capacitor/cli is the Command Line Interface for Capacitor, a crucial tool for managing Capacitor projects. It provides several key functionalities:
>
>Project initialization: The CLI allows you to initialize new Capacitor projects with the "npx cap init" command[5](https://github.com/ionic-team/capacitor).
>  
>. Platform management: It enables adding native platforms to your project, such as iOS and Android, using commands like "npx cap add android" or "npx cap add ios"[5](https://github.com/ionic-team/capacitor).
>  
>. Project synchronization: The CLI facilitates syncing your web app with native projects using "npx cap sync"[1](https://app.studyraid.com/en/read/11146/345586/definition-and-purpose-of-capacitor).
>  
> Plugin management: It helps in adding, removing, and updating Capacitor plugins[3](https://ionic.zone/capacitor/overview).
>  
>  Build and run: The CLI assists in building and running your app on different platforms[3](https://ionic.zone/capacitor/overview).
>  
>Project configuration: It allows you to manage and update your project's configuration settings[3](https://ionic.zone/capacitor/overview).
   > 
> Code copying: The CLI handles copying your web app's code to native platforms and updating plugin code in native projects[3](https://ionic.zone/capacitor/overview).
>
>  NOTE: @capacitor/cli ** does need ** a separate step to install in the `root` package.json
>
>The Capacitor CLI is typically installed as a development dependency in your project, ensuring that different projects can use different CLI versions if needed**


> [!faq]- Notes on capacitor.config.json file.
> The `capacitor.config.json` file will probably initially look something like this:
>
>```json
>{
 > "appId": "com.abcdefg2.org",
  >"appName": "My Gmap9 Test",
  >"webDir": "www"
>}
>```
>
> The `webDir` will probably need to be changed at some point to `"dist/spa"`.
> The `dist/spa` directory is created in a following step.
> As far as I can determine, the `"www"` is a default webpack configuration,
and `"dist/spa"` is a Quasar thing.
> 
> If you don't change the `webDir`, you will might get a common bug that results in a white-screen on android.
>
> There is a specific section, **Part 3 E Create /dist directory** which will discuss the `webDir` in more detail.



#### P3C - Step 2: Add Capacitor config In Project Root

==You MUST manually install the `@capacitor/cli` and the `@capacitor/core` modules in the project root!==  ***Make sure root install matches the version in `/scr-capacitor`

Change directories to your project root.

In your project root directory first run:
```bash
npm install @capacitor/cli@6
```

Then run:
```bash
npm install @capacitor/core@6
```

> [!warning]- Important Notes on CLI & Core in Root
> 
> **CRUCIAL!!!     DO NOT IGNORE THIS NOTE!!!**
> Add Capacitor cli and core to the package.json file in Root Directory for Vite web build.
> 
> Running `"quasar mode add capacitor"` in the root directory only creates src-capacitor folder and the capacitor related files configurations in the `/src-capcitor` directory.
> 
> The command `"quasar mode add capacitor"` **does not** however update the `package.json` file or update the node_modules in the project root, which turns out to be (as of Feb 2025) absolutely crucial.
> 
> Per research:
> *************
> Point 1
> Why`@capacitor/core` Must Be Installed in the Root of the Quasar Project.
> 
> Ensures Compatibility with Quasar's Web Build System
> - Quasar's frontend relies on Webpack (or Vite) for bundling the application.
> - The Capacitor plugins and API calls (import { Camera } from '@capacitor/camera') are part of this web build process.
> - If `@capacitor/core` is not in root node_modules, Quasar's Webpack build may not resolve, leading to "module not found" errors.
> *************
> 
> Point 2: Install in Project Root? Or just in `/src-capacitor`?
> 
>  Which capacitor plugins features-plugins-components-api (what ever you want to call them) do you need to install in the project root so it just updates the root `package.json` and the node_modules?
> 
> And which capacitor plugins to only install into the `/src-capacitor` folder so it only updates the `package.json` file and node_modules in the `/src-capacitor` folder?
> 
> It turns out this is nearly pure guess-work.
> 
> There is no definitive chart or guide. As of Feb 2025, here's a little bit of what I've learned through arduous trial and error and endless floundering around on the internet.
> 
> The heuristic rule of thumb seems to be:
> 
> - Native? or not Native?
 >  If the capacitor feature is going to exercise native phone features, such as haptics or camera, only install in just `/src-capacitor`.
> 
> Examples:
> Install in both project root and src-capacitor:
> - `@capacitor/core`
> - `@capacitor/geolocation`
> 
> Install in just `/src-capacitor`:
> - `@capacitor/android`

> [!info]- Recommend ReExamine Root package.json
>
>The `package.json` file dependencies in the ==*project root*== should subsequently look something like the json file below.  Note the addition of the capacitor cli and core.
>
>```json
>{
>"dependencies": {
 >   "@capacitor/cli": "^6.2.0",  <- match package.json in src-capacitor
 >   "@capacitor/core": "^6.2.0", <- match package.json in src-capacitor
>   "@quasar/extras": "^1.16.4",
>   "axios": "^1.2.1",
>   "pinia": "^3.0.1",
>   "quasar": "^2.16.0",
>   "vue": "^3.4.18",
 >   "vue-router": "^4.0.0"
>},
>  "devDependencies": {
>   "@eslint/js": "^9.14.0",
>    "@quasar/app-vite": "^2.1.0",
>   "autoprefixer": "^10.4.2",
>    "eslint": "^9.14.0",
>    "eslint-plugin-vue": "^9.30.0",
>    "globals": "^15.12.0",
>    "postcss": "^8.4.14",
>    "vite-plugin-checker": "^0.8.0"
>  }
>}
>```


#### P3C - Step 3: Verify installation

Check the capacitor CLI version in project `root`:
```bash
npx cap --version
```

Change directories into the /src-capacitor folder:
```bash
cd src-capacitor
```

Then run to check capacitor in `/src-capacitor`:
```bash
npm list @capacitor/core
```

The capacitor core version, which should match package.json.


### Part 3D - Add Capacitor/android to project

Now we can start configuring things to actually create an Android app.  These steps will allow Android Studio to launch.

NOTE: The **`@capacitor/android`** is ==**native**== and only needs installed in the `/src-capacitor` folder.

The install of capacitor android is a two step process.  As an analogy: think about this as repairing your car:
- First go to the parts store and get the car parts.
- And then you actually bolt the parts to the car.

#### P3D - Step 1: Install Android Platform Package

The step is like going to the automotive store to get your car parts.

Be sure and change directories into the `/src-capacitor` directory-folder:

```bash
cd src-capacitor
```
then
```bash
npm install @capacitor/android@6.0.0
```

The `package.json` file in `/src-capacitor` folder should then look something like this:

```json
{
  "name": "gmap9",
  "version": "0.0.1",
  "description": "A Quasar Google Map test",
  "author": "abcdefg2 <abcdefg2@icloud.com>",
  "private": true,
  "dependencies": {
    "@capacitor/android": "^6.0.0",   <- android added
    "@capacitor/app": "^6.0.0",
    "@capacitor/cli": "^6.0.0",
    "@capacitor/core": "^6.0.0"
  }
}
```

##### P3D Step 1 Notes
> [!warning]- Notes about capacitor android versioning
> Warning Note: 
> Just running the following will default in android v7.
> ```bash
> npm install @capacitor/android
> ```
> 
> This v7 android will conflict with the the v6 capacitor/core that Quasar defaulted.
> 
> Check your `package.json` file in `/src-capacitor`
> 
> Run following command to stay compatible with package.json versions in src-capacitor folder, if of course your `cli` and `core` are at v6:
> 
> ```bash
> npm install @capacitor/android@6.0.0
> ```
> 
> Link to other notes & rantsabout versioning issues:
> [[#P3C Step 1 Notes]]
> [[#P3G Step 1 Note 1 Versioning Challenges read]]
> 
> Here is a link to the official Capacitor documentation on the `@capacitor/android` package, (and it really doesn't tell you much about versioning):
> https://capacitorjs.com/docs/android#adding-the-android-platform


> [!warning]- Note: just add android to `/src-capacitor`
> 
> ### Warning: Why Not Install @capacitor/android in the Project Root?
> 
> Per research:
> ***********
> Unlike @capacitor/core, which is needed in both the web and native contexts, @capacitor/android is a native platform package that is only needed by the Android project inside src-capacitor.
> 
> 🚨 Problems If Installed in the Root:
> - Not Needed for Web Builds: The root Quasar project does not need @capacitor/android, as it does not run any Android-specific code.
> - Potential Dependency Conflicts: Installing @capacitor/android at the root can sometimes cause conflicts when running npx cap sync, as Capacitor expects platform dependencies inside src-capacitor.
> ***********


> [!info]- Notes on native runtime
> Per research:
> *************
> Why `@capacitor/whateverplugin` usually needs to be Installed In just `/src-capacitor`:
> 
> (a) Native Runtime Dependency for Capacitor's Native Code
> - The src-capacitor directory is where Capacitor's native project (Android/iOS) is initialized.
> - The native build system (gradle for Android, CocoaPods for iOS) may require @capacitor/core to be present.
> - When you run npx cap sync, it scans src-capacitor to gather necessary dependencies for native builds.
> 
> (b) Ensures Proper Dependency Resolution for Native Plugins
>  Some Capacitor plugins rely on @capacitor/core being locally available inside src-capacitor to properly initialize.
> - If @capacitor/core missing, commands like `npx cap sync` or `npx cap run` could have errors where native plugins cannot find Capacitor core runtime
> 
> (c) There are exceptions (of course) to installing plugins in the project root: native platform package. (meaning: if the plugin is native android, probably don't install in project root).
> *************

#### P3D - Step 2: Create the Android Project Structure

This step is like actually bolting the car parts to your car.

Run the following in the `/src-capacitor` folder:

```bash
npx cap add android
```

The above command `npx cap add android` will actually create the `/android` folder-directory within the `/src-capacitor` folder.

When you run `npx cap add android`, Capacitor is looking at the `capacitor.config.json` file.

```
your-project/
├── .quasar
├── node_modules
├── src/
├── src-capacitor/
│   ├── node_modules       
│   ├── www
│   ├── android/               <- location of android
│   ├── capacitor.config.json
│   ├── package-lock.json
│   └── package.json
├── index.html
├── package-lock.json
├── package.json
└── quasar.config.js
```

###### P3D Step 2 Notes
> [!info]- Android Project Structure Detail
> **Note 1: Android Project Structure**
> 
> Inside the `/src-capacitor` folder:
> After running `npx cap add android`, the generated `/android` folder follows a standard Android project structure that should look something like this:
> 
> ```
android/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/app/
│   │   │   │   ├── MainActivity.kt
│   │   │   ├── AndroidManifest.xml   <- update capacitor plugins
│   │   │   ├── res/
│   │   │   │   ├── drawable/
│   │   │   │   ├── layout/
│   │   │   │   ├── mipmap/
│   │   │   │   ├── values/
├── build.gradle
├── settings.gradle
> ```
> When you install a capacitor plugin you will probably need to manually update permission within the `AndroidManifest.xml` file.

> [!info]- MainActivity file
> **Note 2: The MainActivity.kt File (Entry Point)**
> 
> This is the Kotlin (kt) language for Android...you might default in Java. Either will work.
> 
> Located at:
> `src-capacitor/android/app/src/main/java/com/example/app/MainActivity.kt`
> 
> This file extends BridgeActivity, which is provided by Capacitor:
> 
> ```kotlin
> package com.example.app
> import com.getcapacitor.BridgeActivity
> class MainActivity : BridgeActivity() {
> }
> ```
> 
> What The above Means:
> - BridgeActivity is a Capacitor-provided class that acts as the bridge between the web code (your Quasar app) and the native Android layer.
> - This is where Capacitor loads the web content (index.html from your Quasar build).
> - You can extend this class to register additional native plugins.

> [!info]-  AndroidManifest.xml file
>**Note 3: AndroidManifest.xml (Native Configuration)**
> 
 >Located at:
 >`/src-capacitor/android/app/src/main/AndroidManifest.xml`
 >
 >This file configures important settings like:
 >- Permissions (e.g., Camera, Geolocation)
 >- App name, package name
 >- Main activity that launches on startup
 >
 >Example snippet below (please excuse the tick mark escape characters):
 > Note again when adding plugins, you will probably need to update permissions:
 > ```xml
>`<uses-permission...>
>```
 >
>```xml
> `<manifest xmlns:android="http://schemas.android.com/apk/res/android">
 >`<package="com.example.app">`
>	
>	 `<uses-permission android:name="android.permission.INTERNET" />`
>
>	`<application
>		 android:allowBackup="true"
>		android:theme="@style/AppTheme">
>		`<activity
>			android:name=".MainActivity"
>			 android:launchMode="singleTask"
>			android:theme="@style/AppTheme.NoActionBar">
>			 `<intent-filter>				
>			 `<action android:name="android.intent.action.MAIN" />
>			 </intent-filter>
>		 `</activity>
>	 `</application>
> `</manifest>`
>```

> [!info]- Kotlin or Java File
>### P3D Step 2 Note 4: Capacitor Plugins and Kotlin
>
>Per research:
>*************
>If you install native plugins (e.g., Camera, Filesystem), Capacitor will automatically integrate them.
>For example, if you install the capacitor camera plugin:
>
>```bash
>npm install @capacitor/camera
>npx cap sync
>```
>
>It will register in Kotlin automatically. If needed, you can manually add them to MainActivity.kt:
>
>```kotlin
>import com.getcapacitor.BridgeActivity
>import com.getcapacitor.Plugin
>import com.getcapacitor.community.camera.CameraPlugin
>
>class MainActivity : BridgeActivity() {
 >   init {
 >       registerPlugin(CameraPlugin::class.java)
 >   }
>}
>```
>*************

#### P3D Step 3 : Verify android installation

Verify installation in the `/src-capacitor` folder:

```bash
npm list @capacitor/android
ls android/  # Should show complete Android project structure
```

> [!info]- How Android Works in a Quasar/Capacitor App:
>- ==Your Quasar app runs inside a WebView on the Android.==
>- Note: some developers do not like WebView for various reasons, such as performance.  
>- Capacitor provides a JavaScript-to-Native bridge, allowing Quasar to interact with the native Android layer.
>- Kotlin is only used when you need to modify native functionality (e.g., adding custom plugins or tweaking the Android behavior).


### Part 3E - Create Dist/Spa Directory

Additionally, there is yet another step:
- Create a `/dist` directory

To build your Quasar app for production generate the /dist directory with terminal command in the root directory:

```bash
quasar build
```

This will create a new /dist directory:

```
your-project/
├── .quasar
├── dist/             <- new dist directory
├── node_modules
├── src/
├── src-capacitor/
├── index.html
├── package-lock.json
├── package.json
└── quasar.config.js
```

==Then Very Important!
     Update the `capacitor.config.json` file!!!== 
     In your `/src-capacitor` folder, it must to point to the correct web directory: 
		`"webDir": "dist/spa"`

The `capacitor.config.json` file should look something like this:
		`{`
			`"appId": "com.yoururl.gmap",`
			`"appName": "quasargooglemap",`
			`"webDir": "dist/spa"`
		`}`


> [!info]- Notes on dist/spa
> Notes: per my research here's an explanation for the above step regarding `dist/spa`:
> *****
> When you scaffolded your project using `quasar mode add capacitor`, it defaulted to `"www" `instead of `"dist/spa"` for historical and compatibility reasons.
> 
> The `"www"` directory is a common default for many web-based mobile frameworks, including Cordova, which Capacitor was designed to be compatible with. This default setting allows for easier migration from Cordova projects and maintains consistency with other hybrid mobile development tools.
> 
> However, Quasar's build process typically outputs to the `"dist/spa"` directory for Single Page Applications. This mismatch between Quasar's output and Capacitor's default expectation is why you need to manually update the `webDir` in the `capacitor.config.json` file.
> 
> To align Capacitor with Quasar's build output, you should change the `webDir` setting in your `capacitor.config.json`
> 
> If you do not run "quasar build", and just launch a dev server locally, you can probably keep `"webDir": "www"` in `capacitor.config.json` file.
> *****


### Part 3F - Sync Your Project

Now sync your project with Capacitor to ensure everything is up-to-date run command in the src-capacitor directory:

```bash
cd src-capacitor
npx cap sync
```

> [!info]- Sync Details - What ==npx cap sync== does
>### P3F Note 1: Sync Process Details
>Run `npx cap sync` in the `/src-capacitor` folder to synchronize your web app with the Capacitor project. 
>This command does two things:
>- Copies your web assets to the native platforms
>- Updates native plugins and dependencies
>
>The ==npx cap sync== command relies on the `capacitor.config.json` file (in `/src-capaitor` folder), which contains the following crucial piece of information:
>
>        `"webDir": "dist/spa"`
>
>The `npx cap sync` command is crucial because it:
>- Copies the latest web assets from your specified webDir to the native platform folders.
>- Updates Capacitor and Cordova plugins, ensuring all native dependencies are in place.
>
>	**Do Not Run `npx cap sync` In Project root.**
>	Note that if you run ==npx cap sync== in the project `root` directory, you will get an error, because the root directory does not have a `capacitor.config.json` file.  The error message seems rather confusing (it should say something like: "Yo dummy, I couldn't find the capacitor.config.json file so I couldn't do anything).  But if you read the error msg carefully it has a clue.
>	
>`error Could not find the web assets directory: ./www. Please create it and make sure it has an index.html file. You can change the path of this directory in capacitor.config.json (webDir option). You may need to compile the web assets for your app (typically npm run build). More info: https://capacitorjs.com/docs/basics/workflow#sync-your-project`
>
>The clue in the above error is the command `npx cap sync` looking for the **`webDir`** (aka web assets directory) in the `capacitor.config.json` file, which is only in the `/src-capacitor` folder to create the web assets (for use in the WebView)
>	
>**More tedious details**:
 The command `npx cap sync` is responsible for **synchronizing your web app with the native platforms (Android/iOS)**. Specifically, it performs the following steps:
> 
> 1. **Copies Web Assets (`dist/spa`) to Native Platforms**
>     - It then copies the built web files (`index.html`, CSS, JavaScript, etc.) into each native platform’s web runtime directory:
>         - For **Android** → `android/app/src/main/assets/public/`
>         - For **iOS** → `ios/App/public/`
>
> 2. **Updates Dependencies for Installed Plugins**
>     - It looks at `package.json` to find any installed Capacitor plugins (e.g., `@capacitor/camera`, `@capacitor/geolocation`).
>     - Then, it ensures that the native Android/iOS projects include those plugins.
>
> 3. **Runs `npx cap copy` Automatically**
>     - This is the same as running `npx cap copy` manually, meaning it updates the web assets in the native platforms.
>     
> 4. **Runs `npx cap update` Automatically**
>     - It checks for any new Capacitor dependencies and updates the Android/iOS native projects accordingly.
>     
> 5. **Ensures Android/iOS Project Files are in Sync**
>     - It updates native platform files, such as `AndroidManifest.xml` and `Info.plist`, with any configuration changes from your Capacitor plugins.
> Optionally, you can run `npx cap sync android` in the `/src-capacitor` folder to specifically sync the Android platform.
> 
>****How `capacitor.config.json` is Used**
Your `capacitor.config.json` file contains essential project settings:
>
> - **`appId`**: `"com.abcdefg.gmap"`
>     
>     - This is the unique application identifier (package name for Android, bundle ID for iOS).
> - **`appName`**: `"quasargooglemap"`
>     
>     - The display name of your app.
> - **`webDir`**: `"dist/spa"`
>     
>     - This tells Capacitor **where** to find the built web files.
>     - Since you're using Quasar, `"dist/spa"` is the directory where Quasar compiles the production build of your app.
> 
> **Why is this important?**
> 
> - `npx cap sync` **relies on `webDir`** to copy files to the native platforms.
> - If your Quasar build output changes (e.g., if you're using `dist/pwa` instead of `dist/spa`), you'd need to update `webDir`.

> [!warning]- Directory `/src-capacitor` importance
>### P3F Note 2: Directory Location Importance
>
>Running `npx cap sync` in the root directory of your Quasar-Capacitor project doesn't work because Quasar manages the Capacitor integration differently from a standard Capacitor project. Here's why:
>
>- Quasar's project structure: Quasar isolates Capacitor-related files in the `/src-capacitor` directory, including the relevant `capacitor.config.json` file.
>
>- Capacitor configuration: The capacitor.config.json file in the `/src-capacitor` folder is the one Capacitor uses directly when building and running our app.
>
>- Quasar CLI integration: Quasar CLI handles the Capacitor sync process when you run commands like `quasar dev -m capacitor` or `quasar build -m capacitor`.


> [!info]- List of npx capacitor commands
> **Core Capacitor Commands**
> 
> These are the main commands used for managing Capacitor in your project:
> 
> - **`npx cap init [appName] [appId]`**  
 >    Initializes Capacitor in your project by creating a `capacitor.config.ts/json` file.
>     
> - **`npx cap add [platform]`**  
>     Adds a Capacitor platform (`ios`, `android`, `web`) to your project.  
>     Example:
>      `npx cap add android`
 >    
> - **`npx cap update`**  
 >    Updates Capacitor and all installed plugins to the latest compatible version.
>     
> - **`npx cap sync`**  
 >    Copies web assets (`dist` folder) to the native platform directories and updates dependencies.
>     
>     - This should be run after making changes to web assets or Capacitor plugins.
> - **`npx cap copy`**  
>     Only copies web assets to the native platforms but does **not** update dependencies.
>     - Use this when you update frontend code but don’t need to reinstall plugins.
> - **`npx cap open [platform]`**  
>     Opens the native IDE for the given platform.
>     
>     - Example:
>         
>         sh
>         
>         CopyEdit
>         
>         `npx cap open android  # Opens Android Studio npx cap open ios      # Opens Xcode`
>         
> 
> ---
> 
>  **Development & Debugging Commands**
> 
> These help with debugging and running your app:
> 
> - **`npx cap doctor`**  
>     Checks for common issues in your Capacitor project setup.
>     
> - **`npx cap run [platform]`**  
>     Builds the app and runs it on a connected device or emulator.
>     
>     - Example:
>         
>         sh
>         
>         CopyEdit
>         
>         `npx cap run android`
>         
> - **`npx cap serve`**  
>     Serves the web app locally for testing (useful for `capacitor://` or `http://` debugging).
>     
> 
> ---
> 
> **Plugin & Configuration Management**
> 
> Useful for managing Capacitor plugins and settings:
> 
> - **`npx cap ls`**  
>     Lists installed Capacitor platforms and plugins.
>     
> - **`npx cap plugin add [plugin-name]`**  
>     Installs a Capacitor plugin.  
>     Example:
>     
>     sh
>     
>     CopyEdit
>     
>     `npx cap plugin add @capacitor/geolocation`
>     
> - **`npx cap plugin rm [plugin-name]`**  
>     Removes a Capacitor plugin.
>     
> - **`npx cap migrate`**  
>     Migrates Capacitor config files from JSON to TypeScript (if needed).
>     
> 
> ---
> 
> **Platform-Specific Commands**
> 
> These commands apply to a specific platform:
> 
> - **`npx cap copy [platform]`**  
>     Copies only web assets to the specified platform.
>     
> - **`npx cap sync [platform]`**  
>     Syncs web assets and updates dependencies for a single platform.  
>     Example:
>     
>     sh
>     
>     CopyEdit
>     
>     `npx cap sync android`
>     
> - **`npx cap open [platform]`**  
>     Opens the corresponding native project in its IDE.
>     
> 
> ---
> 
>  **Troubleshooting Tip**
> 
> If you are facing issues with Capacitor commands, try:
> `npx cap doctor`
> This will scan for common misconfigurations.
> 

  

### Part 3G - Install Capacitor Plugins 

And finally, now we can start adding Capacitor plugins that can work on a phone!  There are so many cool features that Capacitor has to offer. Here's a link: [https://capacitorjs.com/docs/plugins](https://capacitorjs.com/docs/plugins)

Each time you add/install a capacitor plugin:

- You may need to run an `npm install` in two places!
- Once in `/src-capacitor`, then again in the `root`.
- And you should carefully inspect both `package.json` files to confirm versions.

#### P3G - Step 1: Install Proper Plugin Versions

 **Example: @capacitor/geolocation**
 
Let's use the ==geolocation== plugin as an example for how to go about installing a plugin into your scaffolded Quasar project (*which again: defaulted in cli and core at v6*).

cd into your src-capacitor directory:
```bash
cd src-capacitor
```

Then run the install of the capacitor plugin. Given my package.json capacitor/core version is v6 recommend run:
```bash
npm install @capacitor/geolocation@6.x
```

The same pattern (appending @6.x) should work for all the capacitor plugins.

##### P3G Step 1 Note 1: Versioning Challenges: read:
> [!warning]- More Versioning Rants
> 
>==⚠️ Warning:== Just blindly following the Capacitor documentation might get you into a versioning conflict.
>
>Just running `npm install @capacitor/geolocation` will default in ==v7== (as of Feb 2025).
>
>This v7 will conflict with the *capacitor core* defaulted in with `quasar mode add capacitor` command, which  defaults in capacitor-core at ==v6== (as of Feb 2025).
>
> Oh, and good luck trying to find a comprehensive guide to a proper versioning for the software stack of: 
> ...Node,
> .....Vite,
> ........Quasar, 
> ................Vue,
> ....................Capacitor, 
> ..................... Capacitor-Android 
> .........................Android-Studio
> ............................Android SDK
> ...............................Gradle
> .................................JDK 
> .....................................Java & Jetbrains
> ......................................JVM
> .........................................Kotlin
> ... there simply isn't any comprehensive guide as far as I could discern after many hours of flogging the internet. 
> 
> It's mostly trial and error. The documentation IMO is lacking.  
> 
> This guide represents literally weeks of many, many scaffolding attempts to land a project that works (as of Feb 2025).  
> 
> You're Welcome.
> 
> link to other rants about versioning dependencies:
> [[#P3C Step 1 Notes]]
> [[#P3D Step 1 Notes]]

#### P3G Step 2: Add Permissions in AndroidManifest.xml file

Yes folks, yet more manual steps! Who said this would be easy? 

For Android, you sometimes, but not always, have to manually update the AndroidManifest.xml file.  
Do your own research! 

Example:
Per Capacitor Documentation at following link: https://capacitorjs.com/docs/apis/geolocation

Find your `AndroidManifest.xml` file, which should be way down under:
`/scr-capacitor`
`/android`
	        `/app`
	            `/src`
	                `/main`

For the geolocation plugin, per capacitor, put the following into the `AndroidManifest.xml` file:
```xml
<!-- Geolocation Plugin -->
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-feature android:name="android.hardware.location.gps" />
```

#### P3G Step 3: Install in Project Root.
And yes my friends, for this particular *geolocation* plugin, you also have to install in the project `root`.

So, cd to your project root, and run:

```bash
npm install @capacitor/geolocation@6.x
```

#### P3G Step4: Inspect your package.json files
At this point I highly recommend you inspect both package.json file, in project `root` and in `/src-capacitor` to insure the plugin is in fact installed. They should look similar to what's below. (Note: a slight variation in capacitor versions between `root` and `/src-capacitor` didn't seem to cause issues).

Package.json in project `root`:
![[json-root.png]]
Package.json in `/src-capacitor`:
![[jsonsrc-capacitor.png]]


#### Conclusion to Part 3: Installing Quasar and Capacitor

And finally, always after installing plugins or making other updates, be sure and run in your `/src-capacitor` folder:

```bash
npx cap sync
```

For notes about the `npx cap sync` command, reference [[#Part 3F - Sync Your Project]] again for notes on "What `npx cap sync` does". 

Wasn't that a journey! And now, finally you might actually be able to do some actual development.



# Part 4: Launch Android App
 
## P4 Step 1 - Launching Your Application in Dev

To finally launch the app in development, run:

```bash
quasar dev -m capacitor -T android
```

The above command translates/parses roughly as follows:
- `quasar`:                ==Hey Quasar==,
- `dev`:                      ==please launch a development server==,
- `-m capacitor`:    ==in mode capacitor==,
- `-T android`:        ==targeting android==.

When you run the above command, a session of Android Studio should automagically launch. 

You should be able to interact with your app in Android Studio, and on the test Android phone at the same time.

![[androidstudio.png]]

## P4 Note A - Important Android phone Setup Notes
![[AndroidPhone.png]]
When setting up your development environment:
- You will plug-tether your test Android phone into your development machine via USB (MacBook, etc).
- Make sure your test Android phone has ==debug enabled==.
- Make sure that ==wifi is enabled== on your test Android phone.
- Make sure that your *development machine* (MacBook, etc) **and** the *Android phone* are on the ==same wifi network.==
- Note that wifi in coffee shops, gyms, airports, etc often won't work!...some sort of port-forwarding security issue (TLDR...outside the scope of this document).
- Note that on the Android Studio you usually have to unplug the USB to your test phone and plug it back in to get it to hot-up and be recognized.

## P4 Note B - Chrome Inspect Devices Tool

Also: **HIGHLY RECOMMEND**: use the chrome inspect devices tool!

Open a browser tab, put in:
```
chrome://inspect/#devices
```

When you launch the app you will be able to select your test Android phone and interact with it and show console log and review error messages from the WebView! This feature is so awesome!  

![[chromeinspect2.png]]

# Credits

Let me thank Luke Diebold for his excellent video tutorials, as they gave a huge head start. Luke is just an outstanding educator and Quasar evangelist.  
https://www.youtube.com/@LukeDiebold

Also a shout out goes to all my AI friends, especially Perplexity (which offer links to it's sources!) and Claude which can produce fairly decent code. 
- Not once did these AI's ever roll their eyes and give back some sort of snarky answer to my endless questions about-the-same-dang-thing. 
- If I had to manually research each technical issue or question on Stackoverflow, or any of the other blogs, forums, etc, I could have been reading them till my eye-balls fell out of my skull and never emerged from the research rabbit-hole with any answers at all.

Apologies to all the kind people of the internet who selflessly contribute to the technical zeitgeist, but without these AI's ability to distill their knowledge into specific answers, this project would have been absolutely impossible. Although the AI's are often frustratingly dead wrong, they also often nail the answers, and even the wrong answers sometimes offer important clues.  In fact, I fully expect this blog too will be consumed into the AI blackhole. 

Oh, but I found Copilot in VS Code kinda useless...just say'n. This is as of Feb 2025, so I'm sure things will improve.

And let's give a thanks to Obsidian!
https://obsidian.md/
I recently discovered this app, and it sure beats any of the other apps I've used over the years for taking notes.  Be sure and install the Obsidian webclipper extension to your browser! Wow...it is sooooo useful. When you find a great web resource, just clip into Obsidian and it's there for you to research and link (tags) into all your other notes.  Also, in fact, this blog was produced in Obsidian. Obsidian is so useful, and it's free! Unbelievable.