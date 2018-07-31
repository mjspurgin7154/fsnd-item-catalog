# Item Catalog Project Overview

This catalog application provides a list of catalog categories.  Each category has a list of category items with description.  The application provides a user registration and authentication system. Registered users will have the ability to post, edit and delete their own category items.  Users log into the application using their google sign in credentials.

## Item Catalog:  Guide
For detailed screen shots, descriptions and directions.  Please read the PDF file titled 'Project Guide'.

## Getting Started:
Copy the db_setup.py, db_populator.py, and application.py files to the 
/vagrant/catalog directory (create the catalog directory under vagrant if necessary.  Open a terminal.

    $ cd <your_path>/vagrant
    ~ $ vagrant up
    ~ $ vagrant ssh
    ~ $ cd/vagrant/catalog
    ~ $ python db_setup.py (creates the db, and db tables)
    ~ $ python db_populator (populates the db)
    ~ $ python application.py (runs the application)

Access the application by visiting http://localhost:8000 locally on your browser.

## The Catalog web application
    The main page lists the Categories in the Catalog along with the latest item added to each category.

    By clicking on a category, the user is directed to a category item page showing a list of the categies plus a list of items for the selected category.  A link is provided to redirect back to the main category page.  By clicking on the 'Add New Item' link the user will either be directed to a google+ sign in page or (if logged in) to a new item create form.  

    By clicking on an item, the user is directed to an item description page.  If the user is logged in and authorized, the page will have links to edit or delete an item. 

## login/logout
    The login (or logout)
     button is visible on all of the application pages.

## Application Code
    Code is written in python, HTML and CSS.  SQLAlchemy and Flask toolkits were utilized.

## File Structure
    <your_path>/vagrant/catalog
        * application.py
        * db_setup.py
        * db_populator.py
        * term_setup.py

    <your_path>/vagrant/catalog/templates
        * layout.html
        * category.html
        * items.html
        * newcatitem.html
        * edit_item.html
        * delete_item.html
        * descriptions.html
        * public_descriptions.html
        * login.html
        * logout.html

    <your_path>/vagrant/catalog/static
        - style.css

## Python Terminal Commands (to access the catalog database)
    from sqlalchemy import create_engine
    from sqlalchemy.orm import relationship
    from sqlalchemy import Column, ForeignKey, Integer, String
    from sqlalchemy.ext.declarative import declarative_base
    from sqlalchemy.orm import sessionmaker
    from db_setup import Base, Category, Item, User
    engine = create_engine('sqlite:///catalog.db')
    Base = declarative_base()
    Base.metadata.create_all(engine)
    DBSession = sessionmaker(bind=engine)
    session = DBSession()

## Code Attribution Statement
    Some of the code in this project was obtained from the Udacity Full Stack Web Developer Nanodegree Program and was modified to work with the submitted project.
