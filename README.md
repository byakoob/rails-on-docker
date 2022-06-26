# Hello-World Application on Rails with Docker

An application that always responds with “hello world” to web requests

## Steps To Test Locally:

Please refer to <a href="https://docs.docker.com/samples/rails/" target="_blank">Quickstart: Compose and Rails!</a>

Note: Will make few changes before building the final image:

- in config/routes.rb will make sure all requests respond with hello world by adjusting the route like this:

 ```
 Rails.application.routes.draw do
  root 'pages#home'
  get '/*path' => 'pages#home'
end
```

- In app/controller crete a new action :

```
class PagesController < ApplicationController
    def home
    end
  end
```

- Finally in app/view create a folder pages with the files below:

home.html.erb

```
<h1>Hello, world!</h1>
```

index.html.erb

```
<h1>Pages#index</h1>
<p>Find me in app/views/pages/index.html.erb</p>
```

## Example:

```
rails-on-docker|feature/hello⚡ ⇒ docker compose up                    
[+] Running 2/0
 ⠿ Container rails-on-docker-db-1   Created                                              0.0s
 ⠿ Container rails-on-docker-web-1  Created                                              0.0s
Attaching to rails-on-docker-db-1, rails-on-docker-web-1
rails-on-docker-db-1   | 
rails-on-docker-db-1   | PostgreSQL Database directory appears to contain a database; Skipping initialization
rails-on-docker-db-1   | 
rails-on-docker-db-1   | 2022-06-26 16:42:52.542 UTC [1] LOG:  starting PostgreSQL 14.4 (Debian 14.4-1.pgdg110+1) on aarch64-unknown-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
rails-on-docker-db-1   | 2022-06-26 16:42:52.543 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
rails-on-docker-db-1   | 2022-06-26 16:42:52.543 UTC [1] LOG:  listening on IPv6 address "::", port 5432
rails-on-docker-db-1   | 2022-06-26 16:42:52.548 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
rails-on-docker-db-1   | 2022-06-26 16:42:52.578 UTC [27] LOG:  database system was shut down at 2022-06-26 16:42:48 UTC
rails-on-docker-db-1   | 2022-06-26 16:42:52.618 UTC [1] LOG:  database system is ready to accept connections
rails-on-docker-web-1  | => Booting Puma
rails-on-docker-web-1  | => Rails 5.2.8 application starting in development 
rails-on-docker-web-1  | => Run `rails server -h` for more startup options
rails-on-docker-web-1  | Puma starting in single mode...
rails-on-docker-web-1  | * Version 3.12.6 (ruby 2.5.9-p229), codename: Llamas in Pajamas
rails-on-docker-web-1  | * Min threads: 5, max threads: 5
rails-on-docker-web-1  | * Environment: development
rails-on-docker-web-1  | * Listening on tcp://0.0.0.0:3000
rails-on-docker-web-1  | Use Ctrl-C to stop
rails-on-docker-web-1  | Started GET "/" for 172.25.0.1 at 2022-06-26 16:43:27 +0000
rails-on-docker-web-1  | Cannot render console from 172.25.0.1! Allowed networks: 127.0.0.1, ::1, 127.0.0.0/127.255.255.255
rails-on-docker-web-1  | Processing by PagesController#home as HTML
rails-on-docker-web-1  |   Rendering pages/home.html.erb within layouts/application
rails-on-docker-web-1  |   Rendered pages/home.html.erb within layouts/application (0.5ms)
rails-on-docker-web-1  | Completed 200 OK in 723ms (Views: 698.8ms | ActiveRecord: 0.0ms)
rails-on-docker-web-1  | 
rails-on-docker-web-1  | 
rails-on-docker-web-1  | Started GET "/asas" for 172.25.0.1 at 2022-06-26 16:43:36 +0000
rails-on-docker-web-1  | Cannot render console from 172.25.0.1! Allowed networks: 127.0.0.1, ::1, 127.0.0.0/127.255.255.255
rails-on-docker-web-1  | Processing by PagesController#home as HTML
rails-on-docker-web-1  |   Parameters: {"path"=>"asas"}
rails-on-docker-web-1  |   Rendering pages/home.html.erb within layouts/application
rails-on-docker-web-1  |   Rendered pages/home.html.erb within layouts/application (0.9ms)
rails-on-docker-web-1  | Completed 200 OK in 159ms (Views: 114.4ms | ActiveRecord: 0.0ms)
rails-on-docker-web-1  | 
rails-on-docker-web-1  | 

```