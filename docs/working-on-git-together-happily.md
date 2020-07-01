## Working as a team without conflicts

Every developer has to work together with other developers sometimes, in this article i will be talking about my recent personal experiences doing just that, i allso included
some best practices and guidelines which might help you in your future collaborations!
Github provides many ways for teams to collaborate on code, with multiple people working on the same exact project. 
During my final assignment of my webdesign minor ive had to work with 4 students on the same codebase.

### Problems with working together on the same codebase

One of the biggest problems ive found while working together on the same codebase is deciding which code conventions to maintain, you should know that every programmer has his own
style of writing code and there is nothing wrong with that. 
The problem arises when everyone is just allowed to write code freely, a couple of problems you could encounter:
* polluting the global namespace. 
* having disjointed naming in functions (camelCase / snake_case). 
* inconsistent styling across all pages.
* Having no clue what your colleagues are developing.

I personally had never worked on a project with multiple people, heres a couple of things we did to make sure we had as best a start with the little experience we had:

We decided we would be using GIT for our version control (ofcourse), Git allowed us to have our own workspace, a branch!

![branch 2](https://user-images.githubusercontent.com/36195440/86265995-dc2ad480-bbc4-11ea-9897-a2a2e625d0ed.png)
>In the image above you can see there is a master branch, this contains the main framework of the application. The two lines "branching" out represent
features that are being worked on, these are encapsulated spaces in which you can change whatever you like without the changes applying to the master branch.

## How did we use branches to our advantage

Starting off our collaboration we had created a branch for each of our team members called "develop-[name]" a branch called develop and a branch called master.
As you could have guessed all of us would work on our own designated branch and would not touch the master branch. In addition to having our own branch we created the develop branch
which we would all push our changes to.

### Pulling and fetching

Whenever a branch has new changes you can type the `git fetch`command, this checks what everybody else has been working on without directly downloading the files, 
it is a less agressive method than `git pull` which pulls changes from a respository.

We would use the develop branch to push our local changes to writing `git pull origin develop` and solving merge conflict on our own branch. We would then `git checkout develop`
and pull our changes to the development branch ie. `git pull origin develop-reinier` and then push those changes to the development branch.

### merge conflicts

Sometimes you stumble upon a piece of code one of your colleagues has been working on which just so happens to be the same code youve been working on... we have ourselves a merge conflict.
A merge conflict would typically look like this.

```javascript
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

> As you can see there is a conflict in the README.md file you will be asked to look at both the changes made to the code and select which lines you wish to keep. 
![merge conflict](https://user-images.githubusercontent.com/36195440/86276477-36cc2c80-bbd5-11ea-8e3a-01ff7731e55a.jpg)

Whenever all conflicts had been fixed we would come together and check if the development staging area contained all of our changes and there were no errors at which point we would
`git push origin master` which updates the master branch of our repository.

## best practises for git collaboration

1. Making clean commits with messages
adding a message to your commit `git commit -m "your message"` lets your team know what you have been working on, its also way easer to revert changes when you know what had been changed
at that point of the timeline. You can alsotype `git log` to list all changes you've made if you write clean commits.

2. Commit often!
If you commit often it allows for easy reverts to earlier stages of coding, this avoids circumstances in which you have been coding for 5 hours and nothing works, ahhh!
Commiting often also means your collaborators can pull your changes and let you know if there are any conflicts that need to be adressed.

3. Write a .gitignore file
A gitignore file server to keep your sensitive data or files from being pushed to your public environment, like a .env file in which you store data like passwords, keys or usernames.

4. Make sure every developer has his own clone of the repository, when someone elses code breaks, yours shouldn't.

## Setting up the backbone of your application

I found that it is very important to land on some conventions you and your collaborators are going to maintain, some files are required for every collaborator to use ie. 
a server.js file, partials or even some main css files.

### Setting up styling guidelines
One propblem you might come across when working on a frontend that has a very specific styling or brand identity is having inconsistent styling across multiple pages.
This is no problem if you have one designer, but there might be cases in which multiple developers work on multiple pages at once.
A great solution to this problem is writing general styling rules in sass variables like so:

```javascript
/* COLORS */
$light-blue: #34b6dd;
$yellow: #f6ae1a;
$red: #e51f4f;
$green: #17686d;
$black: #000;
$white: #fff;

$background-color: #E8E8ED;
$light-grey: #f7f7f7;
$grey: #9c9c9c;

/* OTHER PROPERTIES */
$border-radius-small: 5px;
$border-radius-big: 10px;

$container-padding: 10px;
```
> these are very simple commands which when a webpage has a very destinct brand identity really help you keep colors consistent when a button needs to be the companies certified
blue, simply write `background-color: $blue`

### naming conventions
Every webpage uses a layout system, it could be grids, flexboxes you name it... using the same containers over multiple pages really benefits from having some class or id naming
conventions. In my recent projects ive been using the BEM block naming, these block naming conventions this is a very specific way of naming the classes of blocks and the elements
it contains. an example:
![BEM](https://user-images.githubusercontent.com/36195440/86278899-667d3380-bbd9-11ea-9f02-987d6b25eb73.png)
> In this case the form is the block element, and each element within the block starts its classnames with `form` because these elements have no standalone meaning.

## Wrapping up
Working together can couse many (merge) conflicts, luckily theres tools like git and working conventions developed and tinkered by some of the best developers in the bussiness, 
every collaboration needs a set of rules to not end in complete chaos. I recommend reading the sources ive listed below which speak about topics ive learned to incorporate in my
development carreer over the last two months.

### Sources
[BEM -- Block Element Modifier](http://getbem.com/naming/)

[Git Branch](https://www.atlassian.com/git/tutorials/using-branches)

[Best practices for using git](https://deepsource.io/blog/git-best-practices/)

[How to solve a git merge conflict](https://opensource.com/article/20/4/git-merge-conflict#:~:text=Create%20a%20new%20Git%20repo,see%20what%20it%20looks%20like.&text=Return%20to%20the%20master%20branch,something%20different%2C%20and%20commit%20that.&text=Automatic%20merge%20failed%3B%20fix%20conflicts%20and%20then%20commit%20the%20result.,-Now%2C%20go%20into)
