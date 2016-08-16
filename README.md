# Neo4j Movies Example Application

**Shamelessly modified from https://github.com/neo4j-examples/movies-go-cq**

### Stack

* Go 
* [Golang Neo4j Bolt Driver](https://github.com/johnnadratowski/golang-neo4j-bolt-driver)
* Neo4j-Server
* Frontend: jquery, bootstrap, http://d3js.org/[d3.js]

### Endpoints:

Get Movie

```bash
# JSON object for single movie with cast
curl http://bolt-neo4j-movies.herokuapp.com/movie/The%20Matrix

# list of JSON objects for movie search results
curl http://bolt-neo4j-movies.herokuapp.com/search?q=matrix

# JSON object for whole graph viz (nodes, links - arrays)
curl http://bolt-neo4j-movies.herokuapp.com/graph
```

### Setup

This uses the Go standard library HTTP server, along with the Golang Neo4j Bolt Driver library.

### Run locally:

Start your local Neo4j Server [Download & Install](http://neo4j.com/download), open the [Neo4j Browser](http://localhost:7474).
Then install the Movies data-set with `:play movies`, click the statement, and hit the triangular "Run" button.

Start this application with:

```bash
NEO4J_URL=bolt://localhost:7687/ PORT=8080 go run server.go
```

Go to http://localhost:8080

You can search for movies by title or and click on any entry.

# Deploy to Heroku

```bash
# create a new app with the go buildpack
heroku create -b https://github.com/kr/heroku-buildpack-go.git

# Be sure to set your NEO4J_URL in the Heroku configs.
# I used GrapheneDB to host the Neo4j instance 

# push to heroku
git push heroku master
```
