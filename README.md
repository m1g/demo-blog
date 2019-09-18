# Let's Build: With Ruby on Rails - Blog with Comments

![Let's Build: With Ruby on Rails - Blog with Comments](https://i.imgur.com/DkZSTee.jpg)

**An Andy Leverenz tutorial.** Read the full blog post and watch the screencast at [Web-Crunch.com](https://web-crunch.com/lets-build-with-ruby-on-rails-blog-with-comments)

### Kicking things off with a blog

Ultimately, the point of this tutorial and video is to help anyone new to the framework understand how it operates as well as the necessary conventions required to create a blog using Ruby on Rails. Touching on things such as routing, controllers, views, models, migrations, relations, and more. For this project, we make use of a few `gems` of which help make my life a bit easier as I build out applications. You can find out more about those below.

### Gems used in the project

- [Better Errors](https://rubygems.org/gems/better_errors) - Easier on the eyes when it comes to errors.

- [Bulma](https://github.com/joshuajansen/bulma-rails) - Most of the time I would roll my own CSS or just use bits of a framework. I'm a big fan of bulma so we will be using it a lot throughout this series.

- [Guard](https://github.com/guard/guard) - This gem is useful for live reloading our `scss`, `js`, `css`, and `erb` files, although it's capable of much more! *Guard is required for the Guard LiveReload gem to work*

  Add the following within the development space in the `Gemfile`. Make sure to run `bundle` and restart your server (covered in the video).

  ```ruby
  group :development do
    # Guard is a command line tool to easily handle events on file system modifications.
    gem 'guard', '~> 2.14', '>= 2.14.1'
  end
  ```

- [Guard LiveReload](https://github.com/guard/guard-livereload) - This gem depends on the Guard gem. I use this to automatically reload the browser when Guard senses changes within the code base.

  1. Download the [livereload browser extension](http://livereload.com/extensions/) for your browser. 
  2. Add the following within the development space of the `Gemfile`. Make sure to run `bundle` and restart your server.

  ```ruby
  group :development do
    # reload the browser after changes to assets/helpers/tests 
    gem 'guard-livereload', '~> 2.5', '>= 2.5.2', require: false
  end
  ```

  1. Run `guard init livereload`

  2. Be sure to comment out the following block in the `Guardfile if it gets generated for your project.

     ```ruby
     # comment this whole block out as we won't be making use if minitest
     # guard :minitest do
     # ....
     # end
     ```

  3. **Restart your server** once more for good measure. Run:

     ```ruby
     bundle exec guard
     ```

      to start the "watching" process within your project directory. We use `bundle exec` as a prefix here so guard has access to all of our dependences in the project. 

  4. Make sure your browser extension is active when navigating to your app. If your console reads back something similar to the following, then you are in good shape.

     ```bash
     00:00:00 - INFO - LiveReload is waiting for a browser to connect.
     00:00:00 - INFO - Guard is now watching at '/path/to/your/project/'
     [1] guard(main)> 00:00:00 - INFO - Browser connected.
     ```

- [Simple Form](https://github.com/plataformatec/simple_form) - For simpler forms!

  Our final post form partial is as follows. Bulma specific classes are added to get Simple Form to play nice with the CSS framework.  

  ```erb
  <div class="section">
  <%= simple_form_for @post do |f| %>
    <div class="field">
      <div class="control">
        <%= f.input :title, input_html: { class: 'input' }, wrapper: false, label_html: { class: 'label' } %>
      </div>
    </div>
  
    <div class="field">
      <div class="control">
        <%= f.input :content, input_html: { class: 'textarea' }, wrapper: false, label_html: { class: 'label' }  %>
      </div>
    </div>
    <%= f.button :submit, 'Create new post', class: "button is-primary" %>
  <% end %>
  </div>
  ```

 Continue reading at [Web-Crunch.com](https://web-crunch.com/lets-build-with-ruby-on-rails-blog-with-comments)
