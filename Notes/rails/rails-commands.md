# Rails Command line cheatsheet 
Create new rails app

```
$ rails new name
```

Starts rails server

```
$ rails s
```

Create scaffold which will create  model, view ,controller etc etc etc

```
$ rails g scaffold Product name description:text price:decimal brand
```

Update database with new model. 

```
$ rails db:migrate
```
## Updating database

Adding extra colum to database _eg:_ adding a _brand_ to _product_ model

```
$ rails g migration addBrandToProduct brand:string
```
This generates a migration file, update the databse with `$ rails db:migrate`

Removing columns is a similar process

```
$ rails g migration DeleteBrandFromProduct brand:string
```

Update the databse `$ rails db:migrate`

## Set up

setting up home page
```ruby
root "controller#method"
```

adding users etc see devise docs

## Linking between models

*Eg*: Linking city model  to resturant model where city has mutiple resturants 

```
$ rails g scafold city name:string
$ rails g scaffold resturant name:string city:belongs_to
```
If you don't relate them initally when you generate them you can later 

`belongs_to :city` in resturant class and `has_many :resturants` in city class.

Also need update database to add forgein key to resturant

```
$ generate migration AddCityRefToResturants city:references
```
 which creates a new migration file. Then run to update your database

```
$ rails db:migrate
```

## Rails console

To enter console

```
$ rails console
```
select specific model

```bash
$ user.all
```

rails acive record middleman between layer and db


```
$ user.sum(:points)
$ user.maximum(:points)
```

## Extras

Show all routes in app

```
$ rails routes
```


Add data manually to Db from dB\seeds.rb

```
$ rails db:seed
```
