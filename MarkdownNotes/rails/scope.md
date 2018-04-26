# Scopes

Scoping allows you to specify commonly-used queries which can be referenced as a method which will
return an ```ActiveRecord::Relation```

In an example Product model with a product name attrubute we would put this inside the *product.rb* file(product model)

```ruby
scope(:product_name, -> (name) { where("name like ?", "%#{name}%")})
```
where:

* ```:product_name``` is the method

* ```(name)``` is the argument we are passing

Every thing in the {} would be our Active Record Query ```where("name like ?", "%#{name}%")``` . 

The ***%*** is a wild card. So putting a ***%*** on the start and end of the word will return everything that starts,ends and contains that word. 

***eg:*** 
* ```%word%``` would return hword , hwordh , word , wordh

* ```%word``` would return hword, word
    
* ```word%``` would return word , wordh

* ```word``` would return word

calling out function

```ruby
Product.product_name("some name")
```
Ths would evoke our active record query stated in our Product class.

*** Implementing this in Rails to create a search function***

Searching a Product model

```ruby
scope(:product_name, -> (name) { where("name like ?", "%#{name}%")})
scope(:description, -> (description) { where("description like ?", "%#{description}%")})
scope(:price, -> (price) { where price: price })
```

In our products controller we need to allow the params through, create method under ```private```

```ruby
def filtering_params(params)
   params.slice(:product_name, :description, :price)
end
```
In our index method

```ruby
def index
    @products = Product.all
    filtering_params(params).each do |key, value|
      @products = @products.public_send(key, value) if value.present?
    end
end
```
We iterate through the params dictionary and  to get key value pairs and pass them into the ```.public_send()``` method which evokes the method *key* and passes in the attribute *value*. This will then run the corresponding method defined in our products class and return an  ```ActiveRecord::Relation``` which we save to the ```@products``` model

Do get these params we can pass in a form to the index view that takes in the ***:product_name, :description, :price***

```html
<div class="panel panel-default">
  <div class="panel-body">
    <form class="form-inline">
      <div class="form-group">
        <label for="product_name">Name:</label>
        <input type="text" name="product_name"  class="form-control">
      </div>
      <div class="form-group">
        <label for="description">Description:</label>
        <input type="text" name="description" class="form-control">
      </div>
      <div class="form-group">
        <label for="price">Price:</label>
        <input type="text" name="price" class="form-control">
      </div>
      <input type="submit" value="Filter" class="btn btn-default">
    </form>
  </div>
</div>
```