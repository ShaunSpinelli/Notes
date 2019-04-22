# 5 Steps Nested Attributes 

## Update multiple models from single form

**Follow bold numbered sentences for instructions** 

Normal text for brief explanations.

If we have two models ```User``` and ```Address```. Where a ```User``` (the parent) has_one ```address``` (the child) and we want to create/edit both using one form.

Our ```User``` model contains a ```name```. Our ```Address``` model contains a ```city```, ```state``` and a _foreign key_ referencing its **parent** the ```user```.

**NB:** Its important we add the reference to the parent model through the child and not the other way around!!!!!

**1) Add ```accepts_nested_attributes_for: childmodel``` to the parent model**

```ruby
# app/models/user.rb
class User < ActiveRecord::Base
  # ... code from above omitted
  has_one :address
  accepts_nested_attributes_for :address
end

# app/models/address.rb
class Address < ActiveRecord::Base
  belongs_to :user
end

```
**2) Inside our user form we add this**

**NOTE:** ```f``` is the local variable that we passed for our main ```form do |f|``` Yours might have a different name (eg: form) so you will have to change it keep ``ff`` the same.

```ruby 
#app/views/_form.html.erb
<%= f.fields_for :address do |ff| %>
  <div>
    <%= ff.label :city %>
    <%= ff.text_field :city %>
  </div>
  <div>
    <%= ff.label :state %>
    <%= ff.text_field :state %>
  </div>
<% end %>
```
**3) Create a helper method file called form_helper.rb and add**

Helper method is used so we can create a new address which we need in order to pass through the nested params

```ruby
# app/helpers/form_helper.rb
module FormHelper
  def setup_user(user)
    user.address ||= Address.new
    user
  end
end

```

**4) Update our main user form by removing the existing ```form_for do |f|```  and adding**

We are calling our ```setup method``` so we can create our address model.

```ruby
# app/views/users/_form.html.erb
<%= form_for(setup_user(user)) do |f| %>
```

We need to white list the additional nested params coming through

**5) Update our permitted params by adding ```ourmodel_attributes``` and the attributes it contains**

```ruby
#app/controllers/users_controllers.rb
def user_params
  params.require(:user).permit(:name, address_attributes:[:city,:state])
end

```

## And now you should be golden !!