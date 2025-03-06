## Formatting a Markdown Resume and hosting it via Pelican

## Introduction
This Readme provides a step-by-step guide to formatting, generating and hosting a resume on a static site generator.
This guide is intended for individuals who have little to no experience with static site generators, forges and Markdown. While there are many different static site generators and Forges, for the purposes of this demonstration, we will be using **Pelican** and **Git/GitHub**

At the end of this guide, you should be able to:
* Write a resume using Markdown.
* Use Pelican to convert it to a static website.
* Deploy the website using GitHub pages

This Readme also tries to relates concepts from _Andrew Etter's Modern Technical Writing_.



## Prerequisites
Before you start, ensure you have the following:
* Access to a terminal and a text editor like [Visual Studio Code](https://code.visualstudio.com/).
* Basic understanding of terminal commands like ``cd``, ``mkdir``, ``mv``.
* Familiarity with Markdown.
* Pelican is a Python-based tool, ensure you have python installed.
  Install [Python](https://www.python.org/). (version 3 or later).
* Most modern python installations come with pip pre-installed. To check if its available, run: 
  ```
  pip --version
  ```

  * If you get an error, that means it is not in your system. To install:
    ```
    python -m ensurepip --default-pip
    ```
* To ensure you have the latest version of ``pip`` :
    ```
    pip install --upgrade pip
    ```

* Install Pelican with Markdown support:
  ```
  python -m pip install "pelican[markdown]"
  ```

* Git is needed in order to store the website for version control and host it via GitHub Pages, to check if Git is installed:
    ```
    git --version
    ```
    * If it throws an error, download it from git-scm.com

 * Create an account on [GitHub](https://github.com).
 * Create a repository on GitHub. This is where the files are stored and also where the site will be hosted via GitHub Pages.

## Instructions
### Step 1: Format a Resume in Markdown
Open Visual Studio Code and create a new folder using the in-built terminal, you can pull up the terminal with the ``Ctrl + ` `` shortcut. 

Navigate into the directory using ``cd`` and create a new folder by running: 
``mkdir myResume``

Navigate into the folder you just created and create a Markdown file with the extension ``.md``, for example: ``resume.md``

Open the file on VS Code and start working on the resume, if you want a live preview of how the markdown text would be rendered, bring up the preview with the ``Ctrl + Shift + V `` shortcut.


Etter emphasizes using a markup language rather than raw HTML because they make documentation simpler and easier to maintain. By using markdown, we are following his principle of minimizing complexity while improving collaboration across different platforms.
### Step 2: Set up Pelican

#### Create a Pelican Project:
In your current directory:
  ```
  pelican-quickstart
  ```
This will prompt you to set up the project, answer the following questions for Pelican to set up the site:
* ``Where to create a new website``, press enter since you are already in the desired directory.
* ```What is the website title```, enter a title.
* ``Who is the author of the website``, enter your name or alias.
* Set your language and when prompted for a URL prefix, enter ``Y``.
* URL prefix: ```https://username.github.io/repoName```
  where ``username`` is the name of your github account and ``repoName`` is the name of your github repository.
* Press enter on the next few prompts that come up until you reach ``Generate a tasks.py?Makefile``, press `Y` for that.
* Since we will be uploading the website via Github pages, just press enter on every prompt that comes up until you reach ``Upload using GitHub Pages?``, where you type ``Y``.
* If this is your personal page, type yes.

**Congratulations, you have successfully set up a pelican project!**



#### Move your Markdown file into the content directory of the pelican project:

  ```
  mv resume.md content/
  ```

Instead of manually styling HTML pages, we place our Markdown formatted resume inside the ``content/`` directory, following Etter's recommendation of using automated tools over manual formatting.

#### Generate the static site:
  ``` 
  pelican content
  ```

This command creates an ``output/`` folder containing the HTML files needed to display the site in your browser..

Note that you will have to run ``pelican content`` every time you make a change to the resume and save it. ``Ctrl + S`` is your best friend. Use this save shortcut every time in your text editor.

#### Preview the site locally:
  ```
  pelican --listen
  ```

Open ``https://localhost:8000`` in your browser to view the resume!

### Step 3: Deploy the generated resume using GitHub pages

#### Initialize a Git repository in the project directory:
  ```
  git init
  git remote add origin https://github.com/yourusername/resume.git
  ```

Create a new branch:
  ``` 
  git branch -M main
  ```

Add the files you want to commit (upload) to the repository:
  ``` 
  git add . 
  ``` 
or if later on you would like to commit any changes you made to the resume:
  ```
  git add content/resume.md
  ```
 

Create a commit message:
  ``` 
  git commit -m "changes written here"
  ```

Push the commit to the main branch:
  ```
  git push -u origin main
  ```

#### Deploy to github pages using gh-pages branch:

Install ghp-import:
  ```
  pip install ghp-import
  ```

Publish the site:
```
ghp-import output -b gh-pages
git push origin gh-pages
```

Go to your GitHub repository settings, navigate to the ``Pages`` section, and select the branch from which the site should be deployed. By default, this is usually set to ``gh-pages``, but if it's not, manually select ``gh-pages`` and save the changes.

**You have successfully uploaded your resume online!**

Access it at ``https://username.github.io/RepoName``

If you wish to make changes to the resume, push the changes to the ``main`` branch first and then run the ``ghp-import`` commands again.


By storing our project on GitHub, we follow Etter's recommendations for modern technical documentation. Using Git as a version control system ensures that our changes can be tracked, mistakes can be reversed and multiple collaborators can work on the same project simultaneously.

## Further resources/readings
[Pelican Documentation](https://docs.getpelican.com/en/latest/)

[Markdown Tutorial](https://www.markdowntutorial.com/)

[Alternative Markdown Guide](https://www.markdownguide.org/)

[GitHub Guide](https://devclub.ca/github-tutorial)

[GitHub Pages Guide](https://pages.github.com/)

## FAQs
###  Why is Markdown better than writing raw HTML?

Markdown is a lightweight markup language that allows you to write formatted text in simple syntax. Raw HTML requires extensive tags for formatting but Markdown makes formatting easier and more readable.

### I updated my Markdown Resume, but why can't I see the changes on my website?

If you updated the markdown resume file but don't see any changes on your website,

Try the following:

* Run ``pelican content`` in the terminal to rebuild your static files.
* Ensure the Markdown file is in the correct directory ``content/resume.md``
    



## Credits
[_Andrew Etter's Modern Technical Writing_](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS)

My team members - ``Doomsday Killers`` :  Mohammad Adnan Malik | Daniel Gorban
  

  