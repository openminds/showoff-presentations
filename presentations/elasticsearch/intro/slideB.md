!SLIDE bullets incremental
# What?
* Yet another search server?
* Yes
* But easier

!SLIDE commandline veel-code
# Easier setup
	$ curl -kLo elasticsearch.tar.gz http://github.com/downloads/elasticsearch/elasticsearch/elasticsearch-0.17.2.tar.gz
	$ tar -zxvf elasticsearch.tar.gz
	$ ./elasticsearch/bin/elasticsearch -f
	
!SLIDE bullets
# Schema Free
* SQLite
* MySQL
* MongoDB, CouchDB
* ...

!SLIDE commandline veel-code
# JSON and HTTP
	
	$ curl -XPUT http://localhost:9200/twitter/tweet/2 -d '{
	    "user": "kimchy",
	    "post_date": "2009-11-15T14:12:12",
	    "message": "You know, for Search"
	}'
	
	$ curl -XGET http://localhost:9200/twitter/tweet/_search?q=user:kimchy
	
!SLIDE bullets
#Realtime
* No more indexing (delta, full)

	
!SLIDE commandline veel-code 
# Multiple indexes

	$ curl -XPUT http://localhost:9200/index1
	$ curl -XPUT http://localhost:9200/index2

	$ curl -XPUT http://localhost:9200/index1/tweet/1 -d '{
	    "post_date": "2009-11-15T14:12:12",
	    "message": "Zug Zug",
	    "tag": "warcraft"
	}'

	$ curl -XPUT http://localhost:9200/index2/tweet/1 -d '{
	    "post_date": "2009-11-15T14:12:12",
	    "message": "Whatyouwant?",
	    "tag": "warcraft"
	}'

	$ curl -XGET http://localhost:9200/index1,index2/tweet/_search?q=tag:warcraft
	$ curl -XGET http://localhost:9200/_all/tweet/_search?q=tag:warcraft
	
!SLIDE commandline
# Multiple nodes
# Asynchronously replication

!SLIDE
# Rich api

!SLIDE
#Easy hackable
## Because it is just JSON