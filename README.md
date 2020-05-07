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
