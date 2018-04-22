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

Views for the user are being run in the background to have control over these views and add
them to the project run 

```
 $ rails g devise:views
 ```

## Working with the _user_

set up a controller with user authentication.Add this to controller
```ruby
before_action :authenticate_user!
```
