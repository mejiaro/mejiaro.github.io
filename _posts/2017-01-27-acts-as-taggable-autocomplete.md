---
layout: articles
title:  "Acts as Taggable On with autocomplete"
date:   2017-01-27 16:38:44 -0600
icon: loyalty
description: "The acts-as-taggable-on gem provides easy to setup and great ux for tagging anytype of object when paired with the rails-jquery-autocomplete gem."
---

<div class="">
  <section class="section--center mdl-grid mdl-grid--no-spacing">
    <div class="mdl-cell mdl-cell--12-col">
    	<p>I'd worked with the acts-as-taggable gem before, but a couple of days ago I had to integrate it with the rails-jquery-autocomplete gem. Here are the steps I followed.</p>

      <h5>Add the necessary gems in the Gemfile:</h5>
      <p>
      {% highlight ruby %}

  gem 'acts-as-taggable-on'
  gem 'jquery-ui-rails'
  gem 'rails-jquery-autocomplete'

      {% endhighlight %}
        
      </p>
      
      
      <h5>Run bundle install and the necessary migrations</h5>

        {% highlight ruby%}

  bundle install
  rake acts_as_taggable_on_engine:install:migrations
  rake db:migrate

        {% endhighlight %}

      <h5>Setup autocomplete</h5>

  {% highlight ruby %}

  class Fruit < ApplicationRecord
    acts_as_taggable
    acts_as_taggable_on :traits
  end

  class FruitsController < ApplicationController
    autocomplete :trait, :name, :class_name => 'ActsAsTaggableOn::Tag'

    private
          
      # Never trust parameters from the scary internet, only allow the white list through.
      def candidate_params
        params.require(:candidate).permit(:name, :trait_list => [])
      end
  end
        {% endhighlight %}

        <p>In your config/routes.rb file you also need to add: </p>

        {% highlight ruby %}
  resources :fruits do
    get :autocomplete_trait_name, :on => :collection
  end
        {% endhighlight %}

        <p>Depending on the version of jquery-ui-rails you have need to add either</p>

        {% highlight javascript %}
  //= require jquery-ui/autocomplete
        {% endhighlight %}

        <p>for versions <= 5.0.5 or </p>

        {% highlight javascript %}
  //= require jquery-ui/widgets/autocomplete
        {% endhighlight %}

        <p>for versions higher than that. Run bundle show to know the versions of the gems you're using.</p>

        <p>Now, in the _form.html.erb file of the model that needs the autocomplete add: </p>
        {% highlight ruby %}
  <%= f.autocomplete_field :trait_list, autocomplete_trait_name_fruits_path, 
                            :value => f.object.trait_list.to_s, 
                            'data-delimiter' => ', 
                            ', 'data-auto-focus' => true,
                            :multiple => true %>
        {% endhighlight %}

        <p>In the code above I've added a few extra parameters, multiple: true makes it so the field accepts more than one trait for the fruit, data-delimieter means that each of the traits will be split by a coma and a space, and the :value param allows the field to show the traits that fruit already has, if any. </p>

        <p>It's simple enough, though I had some problems because the front-end framework I was using had an autocomplete of its own, and it was overwriting the one I installed through the gem.</p>

        <p>If you need more info on each of the gems here's a link to their respective documentation: </p>

        <a href="https://github.com/mbleigh/acts-as-taggable-on">acts-as-taggable-on</a><br>
        <a href="https://github.com/bigtunacan/rails-jquery-autocomplete">rails-jquery-autocomplete</a>
    </div>
  </section>
</div>