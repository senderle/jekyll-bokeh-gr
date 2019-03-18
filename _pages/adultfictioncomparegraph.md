---
layout: vis
title: Reader Network
display_site_title: true
display_page_title: true
order: 3
permalink: /adultfictioncomparegraph/
vis_include: vis/nokids_anonymous_tsne_compare_tsne_log_graph.html
---

This Bokeh visualization is based on a different use of t-SNE than our basic map of readers and genre preferences.  Here, the difference between two readers' tastes is calculated according to the specific books they have read rather than the genres of the books.  In fact, our genre categories are left out of the algorithm entirely. The code here caclulates distance by treating all the books and all the users as part of a bimodal network -- that is, a network with two kinds of nodes that only connect to nodes of the other type. Hence a reader can only be directly connected to books, and a book can only be directly connected to readers. The code then uses this network to run a simulation. It begins by "talking" to a random user and asking for a recommendation. The user randomly picks one of the books they've reviewed, and the algorithm talks to other random users until it finds one who has also reviewed that book. It asks that user for a new recommendation and repeats the process... ad infinitum. The probability `p` of going from a given user to another in this scenario gives the distance between them. (More precisely, the distance is calculated using `-log(p))`.

To make things work nicely, we posit that all the users have reviewed one astonishgly popular book that we don't know the title of. This ensures all users are at least slightly connected in the network. You might say that this imaginary book is goodreads.com.

In this visualization readers appear somewhat less segregated by primary genre preference.  Based on exploration of specific user cases, we believe this is mainly because books that Goodreads users have tended to place on different genre shelves are often more similar to each other than to many of the books with which they share a common shelf.  Some "fantasy" novels, for example, are difficult to distinguish from science fiction, while others are difficult to distinguish from romance. A reader whose primary genre is fantasy might therefore be visualized as a blue point very close to many green points (fantasy romance), while another fantasy reader appears as a blue point surrounded by black (science fiction fantasy).    

Scott Enderle, who wrote the code for this t-SNE projection, has called this a map of "browsing distances," and has written a [post](http://www.lagado.name/blog/deriving-browsing-similarity-3/) describing the idea in more detail.
