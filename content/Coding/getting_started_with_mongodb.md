Title: Getting Started with MongoDB  
Date: 2016-10-11 11:30   
Category: Coding  
Tags: tutorial, mongodb  
Slug: getting_started_with_mongodb   
Authors: Ned  
Summary: 

The MongoDB documentation is really, really excellent. Some of the best I've ever come across - it can be found [here](https://docs.mongodb.com/getting-started/shell/). The main reason for this guide is to provide a super concise summary of how to get up and running with Mongo on a Mac.

## Installation
This is super simple with [Homebrew](http://brew.sh/). From the command line, run:

	brew install mongodb
	
(If you want to see what packages you already have installed with brew, use `brew list`).

## Starting MongoDB
Also super easy. First create a directory where you want all the data to be stored. By default, Mongo assumes that this is at `/data/db`, but you can put it in any directory you want. Then run:

	mongod --dbpath <path to data directory>
	
If you then want to connect to the Mongo shell, open another terminal and type `mongo`. This will connect to the running MongoDB instance.

## Creating a Database/Collection
To create a database:
	
	use <db_name>

To drop it (once using):
	
	db.dropDatabase()
	
List databases:

	show dbs
	
Create a collection (without any special options):

	db.createCollection("<collection_name>")

s