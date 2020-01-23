# Quick guide for uploading vue projects to GitHub pages
Found this medium article (https://medium.com/@Roli_Dori/deploy-vue-cli-3-project-to-github-pages-ebeda0705fbd) but for it to work for our stuff we have to change a step.

Pre-Step: make sure you're latest version is commited and pushed upto github.

1. Get to the vue app file in the terminal and create a new local branch in your project and name it ‘gh-pages’. To do this put:
  git branch gh-pages

2. Create a new file in root directory of your project and name it ‘vue.config.js’. 
In ‘vue.config.js’ file paste the following code:
  // vue.config.js
  module.exports = {
  publicPath: ‘’
  } 
  
3. Inside the publicPath you have to put youre repository name. Go to github and look at the URL. Let’s say url is https://github.com/CodyAbb/recipe_generator you would put 
  publicPath: '/recipe_generator/'
You can now save and close the file.

4. Find and open the file .gitignore located in root directory of your project. Next, find and comment the line which has the text ‘/dist’. To do this go to the line with /dist and add a # to the start of the line. 
You can now save and close the file.

5. Run npm run build, and wait for it to finish. If it throws and error double check what you have put in publicPath.

6. Once done we need to ignore certain files when pushing up so the command is: 
  git add dist && git commit -m "Initial dist subtree commit"
  
7. Next do this line:
  git subtree push --prefix dist origin gh-pages
  
8. Go back to the github repository and click the 'settings' tab. Scroll way down and when you hit the GitHub Pages section make sure the ‘gh-pages’ branch is selected. If not switch from master to that and click Save.

9. Now wait a little and refresh the page. If the banner is still blue it is setting it up but when green and saying 'site is published' you are good to go.

 [Website example from mine after doing](https://codyabb.github.io/recipe_generator/)
