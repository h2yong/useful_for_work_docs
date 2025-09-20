https://www.cnblogs.com/caoyusang/p/13610408.html


```bash
docker run -d --name neo4j_medical \
	-p 7474:7474 -p 7687:7687 \
	-v /home/neo4j/data:/data \
	-v /home/neo4j/logs:/logs \
	-v /home/neo4j/conf:/var/lib/neo4j/conf \
	-v /home/neo4j/import:/var/lib/neo4j/import \
	--env NEO4J_AUTH=neo4j/aa123456 \
	neo4j
```

```bash
docker run -d --name neo4j -p 7474:7474 -p 7687:7687 \
	-v /data/neo4j/data:/data \
	-v /data/neo4j/logs:/logs \
	-v /data/neo4j/conf:/var/lib/neo4j/conf \
	-v /data/neo4j/import:/var/lib/neo4j/import \
	--env NEO4J_AUTH=neo4j/aa123456 \
	--env NEO4J_ACCEPT_LICENSE_AGREEMENT=yes \
	neo4j:4.4.25-enterprise
```