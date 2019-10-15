# Rocky Mountain - NA Regional

## Website
- in docs folder
- see docs/README.md for more info

# Use as Template Website for other Regions
- works seamlessly on github but can host wherever you want to
- mostly one page site with major contents in: index.html
- resources for judges, coaches, contestants, site directors, faq are in separate pages

## using the template
- create a github project
- create docs folder inside project
- copy everything from this project (except .git folder) into the docs folder
- learn how Jekyll framework: https://jekyllrb.com/ works (not that bad...)
- try not to rename data field names in yml files. Only change the data values/contents
    - add new fields if the names are not adquate for your needs
- you can test site locally before publishing any changes
- if you have any questions create issues and tag me @rambasnet

## important folders
- data: that contents data/content of the site
- css: css files
- img: image files
- _includes: html include files that breaks the layout of the page into multiple files
- countdown clock: 
    - modify contestDateTime variable in script.html page

## _data/
- contains the text/contents of the site that may need to be updated
- about.yml - data on about section
- host.yml - data for NA and World Final Hosts
- people.yml - data on people section (executive committee members)
- regions.yml - data on regions (regional names and links)
- site.yml - primary site information, name, heading, title, sponsortship contact, social media etc.
- sponsors.yml - data on sponsors (platinum, and gold...)

## css/
- custom.css - custom css to override theme's CSS

## img/
- all images, people, logos, background, etc.

## _includes/
- important include files to note:
- doctype-head.html
- header.html
- footer.html

## dev env

You can push to master to see changes of the web site, but a local tool install in ubuntu for much faster work (and work off the master branch):

```bash
# Ubuntu 18.04 desktop
sudo apt update
sudo apt upgrade -y
sudo apt install -y emacs git cmake openssh-server
sudo apt install -y ruby-full build-essential zlib1g-dev
if ! grep GEM_HOME ~/.bashrc
then
    echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc
fi
sudo gem update --system
gem install jekyll bundler
cd ~/projects # whereever you keep your projects
REPO=na-rocky-mountain-web
test -d $REPO || git clone git@github.com:icpc/$REPO.git
cd $REPO/docs
bundle install

bundle exec jekyll serve --host 0.0.0.0

#in another window
xdg-open http://localhost:4000
````


