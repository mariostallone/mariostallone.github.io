---
layout: post
title: "A Naive Programmer's guide to Git"
date: 2012-01-21 19:16
comments: true
categories: [Technology, Tips]
---
Git is a version control system. More specifically it’s a distributed version control system.

For those of you who don’t know hat versioning is. Here’s a small anecdote to get you up to speed.

I was working in a project where I was the developer and I had a fellow team mate testing my code.
I used to complete my code and  inform him of the updates and ask him to proceed with the testing.
This was what he used to do.
Download the latest version of the code into a folder with the current date as its name.
Test the code and then let me know of any bugs.

This was his folder structure
Proj<XYZ>
|_ 1st Jan
|_ 2nd Jan
|_ 3rd Jan
and so on.

He was manually keeping a log of updated code at every stage. Don’t you think this was kind of redundant ant time consuming?
This is where version control kicks in.
Imagine a scenario where in, I can code, update my changes and add it as a commit to my remote repository.
Inform the tester about the updates, he/she does a checkout of the latest version of the code. Adds review comments to the commit. I read those comments, make the changes and then commit my changes.
Makes more sense doesn’t it?
Well Git is one such tool, which I’ve grown to love. I must thank my friend [Senthil](https://twitter.com/senkumarv "Senthil") for introducing me to Git.

If your on Windows, you need to download and install git. (Link)
Mac comes with git preinstalled :-)
Edit : I’m so used to having Xcode installed on any Mac that I thought Git actually came pre installed with Mac. Correction, it doesn’t, and must be installed from here ([Command Line Tools](https://developer.apple.com/downloads "Downloads")) or via HomeBrew as suggested by my friend [Akash](http://akash.im/ "Akash").
Linux, download and install ([Link](http://git-scm.com/download "Link"))

If your adding git support to an existing project

1. Navigate to your source directory.
2. Type
{% codeblock %}
git init
{% endcodeblock %}
3. It initializes an empty repository
4. Next, type
{% codeblock %}
git add .
{% endcodeblock %}
5. This adds all the current files to git
6. Next, type
{% codeblock %}
git commit –a –m "Initial Commit" # Or whatever message you find suitable
{% endcodeblock %}

If your starting a new project

1. Create a new directory
2. And follow steps from 2 to 9 from above
3. The only differences will be, as and when you add new files, they aren’t tracked by git by default.
4. You need to add them by typing in
{% codeblock %}
git add .
{% endcodeblock %}

Next, I'll talk about adding remote support.
Remote support works best in a Unix environment

1. Create a new folder in your remote machine as <FolderName>.git. The.git is not mandatory.
2. Then key in
{% codeblock %}
git init –-bare
{% endcodeblock %}
3. This initializes a bare repository
4. Head over to your machine and navigate to the project folder
5. Key in
{% codeblock %}
git remote add origin <username>@<host>:<path>
{% endcodeblock %}
6. This adds a remote using ssh to your git repository
7. Once done. Key in
{% codeblock %}
git push origin master
{% endcodeblock %}
8. You’ll be asked for credentials, supply the same. You can skip this by using ssh keys.
9. As and when you make changes to one of your Local copies, commit and then push to the remote.

That’s it. Git is cool to use, and its even cooler to share your code to others via sites like [github](https://github.com "github"), [gitorious](http://gitorious.org "gitorious"), etc.
