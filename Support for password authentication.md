Support for password authentication was removed. Please use a personal access token instead [duplicate]
//https://stackoverflow.com/questions/68775869/support-for-password-authentication-was-removed-please-use-a-personal-access-to


From August 13, 2021, Github is no longer accepting account passwords when authenticating Git operations. You need to add PAT (Personal Access Token) instead, you can follow the below method to add PFA on your system

# Create Personal Access Token on Github
From your Github account, go to 
Settings => Developer Settings => Personal Access Token => 
Generate New Token (Give your password) => Fillup the form => click Generate token => Copy the generated Token, 

it will be something like ghp_sFhFsSHhTzMDreGRLjmks4Tzuzgthdvfsrta
Now follow below method based on your machine:

# For Windows OS
Go to Credential Manager from Control Panel => Windows Credentials => find git:https://github.com => Edit => On Password replace with with your Github Personal Access Taken => You are Done

# For MAC OS
Click on the Spotlight icon (magnifying glass) on the right side of the menu bar. Type Keychain access then press the Enter key to launch the app => In Keychain Access, search for github.com => Find the internet password entry for github.com => Edit or delete the entry accordingly => You are done

# For Linux based OS
For Linux, You need to configure the local GIT client with a username and email address,

$ git config --global user.name ""
$ git config --global user.email ""
$ git config -l
Once GIT is configured, we can begin using it to access GitHub. Example :

$ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
> Cloning into `Spoon-Knife`...
$ Username for 'https://github.com' : username
$ Password for 'https://github.com' : give your personal access token here
Now cache the given record in your computer to remembers the token :

$ git config --global credential.helper cache
If needed, anytime you can delete the cache record by :

git config --global --unset credential.helper




# my github_token
>>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



# Run this command inside your project directory if project was cloned before 13 Aug 2020.
If push failed, then do this
>git remote set-url origin git@github.com:{user_id}/{project_name}.git

And push again. Then it's work.








