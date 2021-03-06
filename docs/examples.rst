Examples
=========

Start using hybra-core by importing it and setting the data path
****************************************************************
::

  from hybra.core import hybra

  hybra.set_data_path('path/to/data')


Load media data from folder 'yle'
*********************************
::

  data_yle = hybra.load('media', folder='yle/')


Load facebook data from folder 'facebook' with filename including 'page_racist'
*******************************************************************************
::

  data_fb = hybra.load('facebook', folder='facebook/', terms=['page_racist'])


Find mentions to cats in Yle data and print them
************************************************
::

  data_yle_cats = hybra.filter_from_text( data_yle , ['kiss'] )

  for data_entry in data_yle_cats:
    print data_entry['text_content']
    print '' ## empty line makes it easier to work on


Find ten most common authors in Facebook data and print them
************************************************************
::

  from collections import Counter

  authors = [] ## create an empty list for the authors

  for data_entry in data_fb: ## go through the loaded Facebook data
    authors.append( data_entry['creator'] ) ## and add authors on the list

  most_common_authors = Counter(authors).most_common(10) ## save 10 most common authors

  for author, count in most_common_authors: ## go through the most common authors
    print author + ' ' + str(count) ## and print them
