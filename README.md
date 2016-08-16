== Neo4j Movies Example Application

=== Stack

* Go 
* https://github.com/johnnadratowski/golang-neo4j-bolt-driver[Golang Neo4j Bolt Driver]
* Neo4j-Server
* Frontend: jquery, bootstrap, http://d3js.org/[d3.js]

=== Endpoints:

Get Movie

----
// JSON object for single movie with cast
curl http://bolt-neo4j-movies.herokuapp.com/movie/The%20Matrix

// list of JSON objects for movie search results
curl http://bolt-neo4j-movies.herokuapp.com/search?q=matrix

// JSON object for whole graph viz (nodes, links - arrays)
curl http://bolt-neo4j-movies.herokuapp.com/graph
----

=== Setup

This uses the Go standard library HTTP server, along with the Golang Neo4j Bolt Driver library.

=== Run locally:

Start your local Neo4j Server (http://neo4j.com/download[Download & Install]), open the http://localhost:7474[Neo4j Browser].
Then install the Movies data-set with `:play movies`, click the statement, and hit the triangular "Run" button.

Start this application with:

[source,shell]
----
NEO4J_URL=bolt://localhost:7687/ PORT=8080 go run server.go
----

Go to http://localhost:8080

You can search for movies by title or and click on any entry.

=== Deploy to Heroku

[source,shell]
----
# create a new app with the go buildpack
heroku create -b https://github.com/kr/heroku-buildpack-go.git

# Be sure to set your NEO4J_URL in the Heroku configs.
# I used GrapheneDB to host the Neo4j instance 

# push to heroku
git push heroku master
----
