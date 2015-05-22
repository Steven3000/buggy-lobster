####Initial setup

* Checkout the lobsters git tree from Github

* Run Bundler to install/bundle gems needed by the project:

         lobsters$ bundle

* Load the schema into the new database:

          lobsters$ rake db:schema:load

* Create a `config/initializers/secret_token.rb` file, using a randomly
generated key from the output of `rake secret`:

          Lobsters::Application.config.secret_key_base = 'your random secret here'

* Define your site's name and default domain, which are used in various places,
in a `config/initializers/production.rb` or similar file:

          class << Rails.application
            def domain
              "example.com"
            end

            def name
              "Example News"
            end
          end

          Rails.application.routes.default_url_options[:host] = Rails.application.domain

* Seed the database to create an initial administrator user and at least one tag:

          lobsters$ rake db:seed
          created user: test, password: test
          created tag: test

* Run the Rails server in development mode.  You should be able to login to
`http://localhost:3000` with your new `test` user:

          lobsters$ rails server
