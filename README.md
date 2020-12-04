# Modifying the GUI documentation

This section contains instructions about how you can modify the newly developed **[GUI documentation](https://synbiohub.github.io/)** for SynBioHub.

*Note: Before beginning to modify the documentation, make sure that you have **[git](https://git-scm.com/)** & **[Hugo static site generator](https://gohugo.io/getting-started/quick-start/)** installed on your machine. For this documentation, we've put to use the **[ACE-documentation](https://themes.gohugo.io/ace-documentation/)** theme. The instructions, about how to install this theme on your system, are given **[here](https://github.com/vantagedesign/ace-documentation)**. Once you clone the repositories, make sure that under any circumstance you don't modify the **config.toml** file.*



1. Open your terminal/cmd.

2. Clone the **[synbiohub-docs](https://github.com/SynBioHub/synbiohub-docs.git)** and **[synbiohub.github.io](https://github.com/SynBioHub/synbiohub.github.io.git)** repositories using the following command:

    ```git clone <repo link>```

3. Navigate to synbiohub-docs folder on your local machine.

4. Then, navigate to the contents folder, which contains various files written in markdown. Here, you can modify a particular file based on your convenience.

5. Make sure to save the changes that you've made locally. 

6. If you want to view the changes that you've made locally, you should follow the follwing steps:

  * Open your terminal/cmd.
  
  * Navigate to the synbiohub-docs folder using the following command:
    
    ```cd synbiohub-docs```
  
  * Then, enter the following command:
  
    ```hugo server -D```
    
  * After entering the command given above, something of this sort shall be displayed on your terminal:
  
  ```
  Start building sites … 

                   | EN  
-------------------+-----
  Pages            | 33  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     | 26  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 207 ms
Watching for changes in /Users/username/synbiohub-docs/{archetypes,content,themes}
Watching for config changes in /Users/username/synbiohub-docs/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop

```

  * Then, naviagte to the documentation locally by entering the following in your web-browser:
  
    ```http://localhost:1313```
  
     Using this you can view, all the changes that you make to the files written in markdown, in real time.
  
7. Then, once you're satisfied with the changes, press ```ctrl+c``` to exit.

8. Now to commit your changes, you need to follow these steps:

  * Enter the following command, to get the fully rendered version for the changes that you've made:
  
     ```hugo -D```
  
  * By using the command given below, you can see the changes that you've made to the repo:
  
    ```git status```
  
  * Then add the changes to you commit, by using this command:
    
    ```git add .```
  
  * Commit your changes, by using the command given below:
  
    ```git commit -m "Enter a brief message about what changes you've made"```
 
  * Push your changes to the repo, by using the following command:
  
    ```git push origin master```
  
9. Then, once you've pushed the changes to this repository, navigate out of this repository, by using the command given below:

    ```cd```
    
10. In your local **synbiohub-docs** folder, there is a folder, titled **public**, which conatins the fully rendered version of the website. Open this folder and copy all the content.

11. Then, navigate to your local **synbiohub.github.io** folder, and paste this content over to this folder.

12. In your terminal/cmd, naviagte to the **synbiohub.github.io** folder by using the following command:

    ```cd synbiohub.gihub.io```
    
13. By using the command given below, you can see the changes that you've made to the repo:
  
    ```git status```
  
14. Then add the changes to you commit, by using this command:
    
    ```git add .```
  
15. Commit your changes, by using the command given below:
  
    ```git commit -m "Enter a brief message about what changes you've made"```
 
16. Push your changes to the repo, by using the following command:
  
    ```git push origin master```
    
    
  
  
  

