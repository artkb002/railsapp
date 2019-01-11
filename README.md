# railsapp

# Requirments:
vagrant

vagrant provider

Vagrantfile adjustment ( optionaly )


# Steps to run machine and login:
#### 0. Git clone
a) master ( prod )
 git clone -b master https://github.com/artkb002/railsapp.git .
 
b) develop ( dev )
 git clone -b develop https://github.com/artkb002/railsapp.git .
 
#### 1. Adjust Vagrantfile ( see SETUP SECTION in Vagrantfile )
#### 2. run vagrant up
#### 3. run vagrant ssh
#### 4. run sudo su - ${VMUSER} ( the same you set in Vagrantfile )

# Steps to update code:
#### 1. Do changes in git repository
#### 2. Update local repo
#### 3. Recompile code
   bundle exec rake assets:precompile db:migrate RAILS_ENV=production
