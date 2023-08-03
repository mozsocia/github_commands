https://stackoverflow.com/questions/42167345/git-set-local-user-name-and-user-email-different-for-each-repo

For just one repo, go into to the relevant repo DIR and:

git config user.name "Your Name Here"
git config user.email your@email.example

For (global) default email (which is configured in your ~/.gitconfig):

git config --global user.name "Your Name Here"
git config --global user.email your@email.example



or just edit the .git\config file and add these three lines somewhere:

[user]
    name = YourName
    email = your@email.com





https://stackoverflow.com/questions/12254076/how-do-i-show-my-global-git-configuration


https://stackoverflow.com/questions/15381198/remove-credentials-from-git