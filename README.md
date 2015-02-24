# Sinatra File Structure

### What does the File Structure Look Like?

The file structure below is an example of what you will normally see in a classic Sinatra application.

```bash
sinatra-classic-file-structure
├── README.md
├── Gemfile
├── Rakefile
├── app.rb
├── config
│   └── environment.rb
├── config.ru
├── db
    ├── migrate
    ├── seeds.rb
    └── test.sqlite
├── models
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
├── spec
│   └── spec_helper.rb
└── views
```

### config.ru

A `config.ru` file is necessary if you are using a deployment tool such as `shotgun` (see `Gemfile`). It specifies to our app handler what files should be run in order to initialize a new server instance of our Sinatra application.

### `app.rb`

The `app.rb` file is where the application configurations, routes, and controller actions are implemented. There is typically a class, which in this case we will call `App`, that represents an instance of your application when the server is up and running. Inside of the `App` class, you can specify your Sinatra application configurations, as well as your routes and controller actions. Then through your controller actions, you would specify which views to be rendered. The `app.rb` file represents the V and C components of the MVC paradigm.

### `config` directory

The `config` directory stores our `environment.rb` file. The logic for setting up our environment (and the corresponding database configurations for each environment) goes in here.

### `db` directory

The `db` directory currently has three items: a `migrate` directory, `seeds.rb` file, and a `test.sqlite` file. The `migrate` directory holds all of our database migration files, which sets up the tables and their corresponding logic in the database. The `seeds.rb` file holds the model objects that we want to pre-load into our database. For example, when you set up a new database, and you want a user named John to be preloaded in your database, you would include this in your seed file: `User.create(:name => "John")`. Finally, the `test.sqlite` is the raw database file into which we both store model data into and query model data from.

### `public` directory

The `public` directory holds our front-end assets. In the example above, it holds a `stylesheets` directory where all of our stylesheets are located. Javascript directories and any other front-end assets would be stored in `public` as well.

### `spec` directory

The `spec` directory stores all of our RSpec testing files and configurations. The RSpec configurations are set in `spec/spec_helper.rb`, and the spec files are organized via semantic directories. For example, tests that test models should be stored in a `spec/models` directory.
