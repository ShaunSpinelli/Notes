# Devise 
 Add devise gem

```
$ bundle add devise
```

Add devise to project and follow instruction in terminal
```
$ rails g devise:install
```
 
Create a model 

_model_ is normally _user_ or _admin_
```
$ rails g devise Model
```
new model now  contains
1) etc
2) etc
3) etc

then run `$ rails db:migrate` to update database

*still need to set up the views*

## Working with the _user_

to add automatic login screen before index is served
```ruby
before_action :authenticate_user!
```
