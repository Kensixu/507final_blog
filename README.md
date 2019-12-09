# 507final_blog
Data Sources: UMICH Library Blog Website: https://www.lib.umich.edu/blogs

## Get Start

In order to setup the database, run user_interface.py. Without cached file, it will create the cache file and database from scratch. This process will take some time, possibly up to 30 minutes. After that, you can run the unit tests in final_proj_test.py.

## Description

The code is structured into two main python programs. user_interface.py & UMlib_blog.py

*UMlib_blog.py: 

scrapes the UMICH Library Blog website and gathers information about each blog posted.

FUNCTIONS:

get_blogs(): This function scrapes the 99 pages of blogs on the UMICH library website. From those pages, it gathers Title, BlogURL, Author, AuthorURL, Date, Description, BlogSite, BlogSiteURL. It then passes this information into the BlogPost class.

enter_data_to_db(): This function takes the to_json() output of a class instance of BlogPost and inputs the data fields for each table (except TagAssociations) for each blog post.

update_records(): This function: deletes duplicate tags, authors, and blogsites from their respective tables; establishes relations for tags, blogsites, authors; fills in data for TagAssociations; and fills in data for number of times tags were used and number of blogs authors published.

*user_interface.py:

Processes queries for the database and displays information both in the terminal and through plotly.

FUCNTIONS:

user_interface(): This function takes commands entered into the command line and filters them to run the functions outlined. Filters commands and parameters with a series of lists.

tags functions: process_tags() and tags_bar_graph() - Retrieve information from the database and display it with plotly bar graph.

authors functions: process_authors() and authors_pie_graph() - Retrieve information about authors from the database and display it using plotly pie graph.

comments functions: process_comments() and comments_line_graph() - Retrieve information about comment counts per month from the database and display it using a plotly line graph.

images functions: process_images() and images_histogram() - Retrive information about the number of images used per blog site (total) and display the total and averages as a plotly histogram.

## User Guide

Commands in user_interface.py

======tags======

    Description: A function that compares the number of tags used for all articles.

    Options:
        orderby=count/alpha - Default: count 
        Description: Specifies whether to order tags alphabetically by typing "Alpha" or order according to the number
        of times the tag has been used in total. Default is by database.

        desc=desc or asc - Default: desc
        Description: Specifies whether you would like your list returned in descending or ascending order. The default
        is descending.

        limit=None or # (Specific Number)- Default: None
        Description: Specifies the amount of results you want returned. The default is all results in the database.

        graph - Default: None
        Description: Specifies if you would like a graph of the data displayed and auto open in your default web browser. 

        ****The program will next ask for the index of the tag you would want to see for all the articles under that tag, 
         or you can type "no" to exit.
         
EXAMPLE:
"tags alpha asc limit=30"
"tags graph"

======authors======

    Description: A function that lists authors names, their urls, and the amount of blogs they have posted.

    Options:
        orderby=count/alpha - Default: count
        Description: Specifies if the information displayed is ordered by the total number of blogs an author has
        published or lists authors name alphabetically, starting with their first name.

        desc=desc/asc - Default: desc
        Description: Specifies whether the results returned should be in descending or ascending order. The default is
        descending.

        limit=None or # (Specific Number)- Default: None
        Description: Specifies the amount of results returned. The default is all the results in the database.

        graph - Default: None
        Description: Specifies if you would like a graph of the data displayed and auto open in your default web browser.
        
        ****The program will next ask for the index of the author you would want to see for all the articles written 
        by him/her, or you can type "no" to exit.
        
EXAMPLE:
"authors alpha asc limit=20"
"authors graph"

======comments======

    Description: A function that returns the amount of comments made per month on all of the blogs published.

    Options:
        limit=None or # (Specific Number)- Default: None
        Description: Specifies the amount of results returned. The default is all the results in the database.

        graph - Default: None
        Description: Specifies if you would like a graph of the data displayed and auto open in your default web browser. 
        
        ****The program will next ask for the index of the month you would want to see for all the articles for that month,
        or you can type "no" to exit.
EXAMPLE:
"comments limit=20 graph"

======images======

    Description: A function that returns the total number of images used for all posts made by a single blog site.

    Options:
        graph - Default: None
        Description: Specifies if you would like a graph of the data displayed and auto open in your browser. 
        
EXAMPLE:
"images graph"

=====most_recent======

    Description: A function that returns the most recent blogs to be published on the Library Blog site.

    Options:
        limit=None or # - Default is None
        Description: Specifies the amount of results returned. Default is all the results in the database.
        
EXAMPLE:
"most_recent limit=25"

======help======

    Description: A command that will bring up all available commands and options.

======exit======

    Description: Exit the program.



