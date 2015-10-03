#### Set Git Credentials saving
```bash
git config --global credential.helper 'cache --timeout 3600'
```

#### Changing origin URL
```bash
git remote set-url origin https://path_to_repository
# check if succeded
git remote -v
```
#### Merging branch between different repos:
in proj2, where you want to merge
```bash
git remote add proj1 path/to/proj1
git fetch proj1
git merge proj1/master # or whichever branch you want to merge
```
#### Init submodule
This is usefull when you have cloned repo containing submodules and you want clone also submodules
```bash
git submodule init
git submodule update
```
#### Add submodule
```bash
# cd to directory where submodule should be stored
git submodule add https://path_to/repo submodule_name
# commit changes
git commit -m "Added submodule submodule_name"
git push origin
```
#### Remove submodule
```bash
# change to path in your repo, where submodule is installed and deinit submodule, if inited
git submodule deinit submodule_name
# remove it
git rm submodule_name
git rm --cached submodule_name
# change path to repository root and remove it from configuration
rm -rf .git/modules/submodule_name
```

#### Update submodules
```bash
git submodule foreach git pull origin master
```