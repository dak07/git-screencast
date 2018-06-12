00:00 Hello, everyone. Welcome to the Git screencast.
This issue is an introduction to Git for those who have not used it yet. 

00:12 Most likely you have already heard that Git is a Version Control System. To put it another way - it is a repository, a database 
of a project development history, that contains all the versions of its files, from the very old ones to the most current.

00:27 We upload the initial version of our files to Git. Then, after we change anything in any of the uploaded files, 
we add the revised version(s). Git will record and keep track of the file's versions.

00:36 The best part of it is that we can always access the repository, review the content, 
and restore any previous version of any of the files. 

00:45 Another great feature is that Git allows not only to store multiple versions, but also to share our data with other developers. 

00:52 For instance, Alice, Jeff and Bob work on the same team. All of them has Git installed, and each is working 
on their part of the project. When one of them completes their part, Git will allow to share their changes with the other 
colleagues easily, as if they copied their files. 

01:06 But Git is so much better than just copying the files. It has built-in feature that automatically detects any conflict 
and allows to merge all the changes. 
Even if 2 developers have revised the same file, Git will detect the conflict early, so they can resolve it. 

01:19 In most simple cases Git will resolve the conflicts automatically. 
Git is called a Distributive Version Control System because it doesn't need a centralized server. 
Each developer has his or her local copy of Git repository that keeps track of the history of the project. 

01:35 Once a developer changes the file, the changes are first recorded on his or her own, local Git repository.
After that, he or she can contact colleagues, send the latest changes to them or received changes from them. 

01:45 Although the centralized server is not necessary, in most cases it is being created for convenience and 
used as focal point of data exchange. 
All developers can upload their changes to the server or retrieve changes made by other developers from it. 

02:00 All major transactions are still performed locally. It means that you could be on an island 
with bad or no internet connection, yet be able to continue development of your project, check the history, 
review all the changes made previously by other team members, add new files or restore the previous version of any of the files. 
Once you are back to the civilization, you can synchronize with the server, share your work with others, and check
what they have done. 

02:21 Last, but not least, Git is a very reliable system when compared to basic file storage. 
Let's say typical disc where all files are being stored got damaged or memory became corrupt. 
If we have tonnes of files we might not even notice anything at first. 

02:36 Git, on the other hand, doesn't just keep copies of our files. It runs a checksum for everything. 
So, if there is corrupt data found anywhere, it will be discovered right away. 
Also, Git is a distributive system, where every developer has his or her own copy of all the changes from other developers. 
As a result, we have a very reliable backup of everything out of the box, automagically! 
If your files got accidentally damaged, you would be able to recover the damaged files easily 
either by getting copies from colleagues or by synchronizing with the server. 

03:00 It is worth noting that Git can help retrieve your data not only after accidental damages but 
also after intentional damages caused by malicious programs or viruses. 
Even if you've been hacked and hacker made some tricky changes to your files, local checksum will keep track of that, 
so these changes can’t pass through unnoticed. 
Even if the local checksum is being hacked, which is very difficult to do as all checksums are tied together, 
it will result in a conflict when synchronizing with other team members.    
So, you will detect these changes, cancel them with the help from your colleagues, and restore the original data.

03:32 Simply put, Git can be trusted! 

03:37 In addition to all of that, Git offers number of helpful features and useful internet services. 
You'll learn all of it with time, but first let's start by installing Git.



