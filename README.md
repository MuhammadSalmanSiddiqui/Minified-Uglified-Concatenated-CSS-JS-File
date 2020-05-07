# Minified-Uglified-Concatenated-HTML-CSS-JS-File
In this workout you will learn to build a distribution folder containing the files that can be deployed on a web server hosting your project. This distribution folder would be built from your project files using various NPM packages and scripts. At the end of this exercise, you will be able to:

--> Clean out a folder using the clean NPM module.

--> Copy files from one folder to another

--> Prepare a minified and concatenated css file from all the css files used in your project

--> Prepare an uglified and concatenated JS file containing all the JS code used in your project

Cleaning up a Distribution Folder:
---------------------------------
--> Install the rimraf npm module by typing the following at the prompt:

    npm install --save-dev rimraf@2.6.2
 
--> Then, set up the following script:

    "clean": "rimraf dist",
  
Copying Files:
--------------
Your project uses font-awesome fonts or any such files. These need to be copied to the distribution folder. To help us do this, 

--> Install the copyfiles NPM module globally as follows:

    npm -g install copyfiles@2.0.0
  
Remember to use sudo on mac and Linux.

--> Then set up the following script:

    "copyfonts": "copyfiles -f node_modules/font-awesome/fonts/* dist/fonts",                                                                
NOTE: 
----
Above, you will change the path of the files which you want to copy in the dist folder as per your choice which are not           compressable.

NEXT:
----
  
Compressing and Minifying Images:
--------------------------------
We use the imagemin-cli NPM module to help us to compress our images to reduce the size of the images being used in our project. 

--> Install the imagemin-cli module as follows:

    npm -g install imagemin-cli@3.0.0
   
Remember to use sudo on mac and Linux. NOTE: Some students have encountered issues with imagemin-cli not installing its plugins due to issues with global permissions on Mac. In that case try:

    sudo npm install -g imagemin-cli@3.0.0 --unsafe-perm=true --allow-root
   
---> Then set up the following script:

    "imagemin": "imagemin img/* --out-dir='dist/img'",                                                                              
    
NOTE:
----
Above, you will change the path of the folder containing full of images which you want to minify and then those minified images will get save into dist/img folder.

NEXT:
----
   
--> Then, install the usemin-cli, cssmin, uglifyjs and htmlmin NPM packages as follows:

    npm install --save-dev usemin-cli@0.5.1 cssmin@0.4.3 uglifyjs@2.4.11 htmlmin@0.0.7
   
--> Add the following two scripts to the package.json file:

    "usemin": "usemin contactus.html -d dist --htmlmin -o dist/contactus.html && usemin aboutus.html -d dist --htmlmin -o       dist/aboutus.html && usemin index.html -d dist --htmlmin -o dist/index.html",
    "build": "npm run clean && npm run imagemin && npm run copyfonts && npm run usemin" 
    
NOTE:
----
Above, you will minify your html pages and save them individually into dist folder. You can add/del more html pages path by using && into above scripts if you have more or less than 3 html pages.

NEXT:
----
    
--> Open index.html and surround the css links inclusion code as follows:

    <!-- build:css css/main.css -->
    <link rel="stylesheet" href="node_modules/bootstrap/dist/css/bootstrap.min.css">     
    <link rel="stylesheet" href="node_modules/font-awesome/css/font-awesome.min.css">
    <link rel="stylesheet" href="node_modules/bootstrap-social/bootstrap-social.css">
    <link href="css/styles.css" rel="stylesheet">
    <!-- endbuild -->
    
--> Do the same change in aboutus.html and contactus.html.
    Similarly, open index.html and surround the js script inclusion code as follows:
    
    <!-- build:js js/main.js -->
    <script src="node_modules/jquery/dist/jquery.slim.min.js"></script>
    <script src="node_modules/popper.js/dist/umd/popper.min.js"></script>
    <script src="node_modules/bootstrap/dist/js/bootstrap.min.js"></script>
    <script src="js/scripts.js"></script>
    <!-- endbuild -->
    
--> To build the distribution folder, you can type the following at the prompt:
    
    npm run build
    
--> This will build the dist folder containing the files that are a self-contained version of your project. You can now copy the       contents of this folder to a web server that hosts your website.


--------------------------------------------END------------------------------------------------------------------------------------


    
    



