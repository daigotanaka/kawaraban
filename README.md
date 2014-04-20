<!--markdown-->
# djangotanaka

A Django based web site good for blogging. What is so good? Here are some
benefits:

1. **Write in your favorite editor**

    Create and edit posts with your favorite text editor, and post them with
    a single command, rather than opening a web browser

2. **Use [markdown](http://en.wikipedia.org/wiki/Markdown) instead of
cumbersome HTML.**

    Markdown is more legible than HTML in the draft, and produces a clean HTML.

3. **Beafutiful preset layouts is one keyword away**

    Like [cover photo](http://daigotanaka.org/full-width-cover)
    or [carousel](http://daigolab.org) layouts?

## How to use

### Install git and get source code

1. Follow [this instruction](https://help.github.com/articles/set-up-git) to
set up github
2. Get the source code

        git clone git@github.com:daigotanaka/djangotanaka.git
        mv djanotanaka my_website

### Install Python

Mac OSX users should follow
[this guide](http://docs.python-guide.org/en/latest/starting/install/osx/)

1. Install [Python](https://www.python.org/downloads/)
2. Install [pip](http://pip.readthedocs.org/en/latest/installing.html)
3. Install Python packages

        pip install virtualenv    
        virtualenv env
        source env/bin/activate
        pip install -r requirements

### Deploy on Heroku

1. Create [a Heroku account](https://devcenter.heroku.com/articles/quickstart)
and install [the Heroku toolbelt](https://toolbelt.heroku.com/)
2. Create an Heroku app and add PostgreSQL

        heroku login
        heroku apps:create your_heroku_app_name
        heroku addons:add heroku-postgresql:dev --app your_heroku_app_name

3. Edit my_website/.git/config to add heroku as the remote repository
Add this at the end of the file:

        [remote "heroku"]
            url = git@heroku.com:your_heroku_app_name.git
            fetch = +refs/heads/*:refs/remotes/heroku/*

4. Deploy

        git push heroku master

## Run the server locally

### Set up [PostgreSQL](http://www.postgresql.org/download/)

### Set environment variables (do it once)

    LOCAL_POSTGRES_DBNAME=your_db_name
    LOCAL_POSTGRES_PASSWORD=your_db_password
    LOCAL_POSTGRES_USERNAME=your_db_username
    export LOCAL_POSTGRES_DBNAME
    export LOCAL_POSTGRES_PASSWORD
    export LOCAL_POSTGRES_USERNAME

### Start server

    source venv/bin/activate
    foreman start

*Point browser to 0.0.0.0:5000 to view site

## Posting, retrieving, and editing articles

### Set environment variables (do it once)

    DJANGO_USERNAME=your_django_username
    DJANGO_API_KEY=your_django_api_key
    export DJANGO_USERNAME
    export DJANGO_API_KEY

### Posting a new article

    python post draft/my-article.txt

### Retrieving a new article 

    python get --slug my-article 

### Editing an existing article 

    python patch draft/my-article 

## Markdown with goodies

### Cover photo layout

Example: http://www.daigotanaka.org/full-width-cover/

Draft:

    <!--markdown coverphoto-->
    ![Cover photo high res image](http://mysite.com/image.jpg)

    ![Mobile low res image](http://mysite.com/image-low.jpg)

    ## Article title

    Text begins here...


### Carousel layout

Example: http://daigotanaka.org/landing/

Draft:

    <!--markdown carousel-->
    ## Article title

    Intro text outside carousel

    A paragraph that is converted to slide #1

    A paragraph that is converted to slide #2

    ...

### Combine cover photo and carousel layouts

Example: http://www.daigotanaka.org/our-garden-in-spring/

Draft:

    <!--markdown coverphoto carousel-->
    ![Cover photo high res image](http://mysite.com/image.jpg)

    ![Mobile low res image](http://mysite.com/image-low.jpg)

    ## Article title

    Intro text outside carousel

    A paragraph that is converted to slide #1

    A paragraph that is converted to slide #2

    ...
