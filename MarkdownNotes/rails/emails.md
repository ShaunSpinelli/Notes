# Email
What is a mailer


***Create a mailer***

```bash
$ rails g mailer UserMailer
```

where:

```UserMailer``` is the name of the mailer.

In the created ```user_mailer.rb file``` we can set up a default from and but in all of our different mailer methods.

```ruby
default :from => 'noreply@foo.com'

    def send_signup_email(user)
        @user = user
        mail(:to => @user.email, :subject => 'Thanks for signing up')
    end

```
We have created a ```send_signup_email()``` method that take in a user as a parameter.

The mail method sets who we are sending it to and what will appear in the title. The actual body and content will be rendered from our mailer views. The mailer method will look for an .html.erb fille with the same name as it. In thus instance a file called ```send_signup_email.html.erb```

You can think of the mailer as a type of controller.

As an example to show how we envoke this method we send an email after a user creates an account by running the method in the ***user model***.

```ruby
after_create :send_welcome
  def send_welcome
    add_role :author
    UserMailer.send_signup_email(self).deliver
  end
```
Using the ```UserMailer``` we created we run the ```send_signup_email``` method and ```.delveier``` .


Using a service like [Send Grid](https://app.sendgrid.com/) we can sent up our mailer ```config\environments``` files by setting up an action mailer base

```ruby
 ActionMailer::Base.smtp_settings = {
    :user_name => ENV['SENDGRID_USERNAME'],
    :password => ENV['SENDGRID_PASSWORD'],
    :domain => 'yourdomain.com',
    :address => 'smtp.sendgrid.net',
    :port => 587,
    :authentication => :plain,
    :enable_starttls_auto => true
  }
```

```user_name``` and  ```password``` are being read from a .env file see [DOTENV](https://github.com/bkeepers/dotenv)