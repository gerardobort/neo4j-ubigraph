# Related article
http://jexp.de/blog/2014/06/rendering-a-neo4j-database-in-ubigraph/

# POM and dependency injection troubleshooting

1. Edit the pom.xml file, remove (temporarily) the line ```<scope>provided</scope>``` from the artifact dependency "ws-commons-util".
2. Run ```mvn clean package```
3. Once you have run the command above, the application should compile, but it won't run given an internal dependecy failure of the "ws-commons-util" package.  Now rollback the step 1 (re-add the scope tag) from the pom.xml.
4. Download http://archive.apache.org/dist/ws/xmlrpc/apache-xmlrpc-current-bin.tar.bz2 (this is the one that @mesirii pointed out on his blog)
5. Extract the tar file and copy/override the .m2/repository with the extracted one (```cp lib/ws-commons-util-1.0.2.jar ~/.m2/repository/org/apache/ws/commons/util/ws-commons-util/1.0.2/ws-commons-util-1.0.2.jar```)
6. Download and run the Ubigraph server.
7. Run the example with ```java -jar target/neo4j-ubigraph-1.0-SNAPSHOT-jar-with-dependencies.jar```
