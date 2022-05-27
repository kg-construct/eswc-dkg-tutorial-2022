# RMLStreamer hands-on

## Scenario-1

1. Fetch RMLStreamer jar: `wget https://github.com/RMLio/RMLStreamer/releases/download/v2.3.0/RMLStreamer-2.3.0.jar`
2. Start docker compose setup: `docker-compose up`
3. Open browser to http://localhost:8081 for Apache Flink dashboard
4. Press 'Submit New Job' in left menu
5. Press '+ Add New' in the upper right corner
6. Select the RMLStreamer jar to upload it
7. Copy mapping rules to Docker: `docker cp data/example/mapping.rml.ttl rmlstreamer_taskmanager_1:/mnt/data/mapping.rml.ttl`
8. Copy data to Docker: `docker cp data/example/input.json rmlstreamer_taskmanager_1:/mnt/data/input.json`
9. Give permissions to write: `chmod -R 777 /var/lib/docker/volumes/rmlstreamer_data/_data`
10. Click on the RMLStreamer jar upload and enter the following Program Arguments: `toFile --mapping-file /mnt/data/mapping.rml.ttl --output-path /mnt/data/output.nt`
11. Press 'Submit' and wait until the job shows 'FINISHED'
12. Copy the generated RDF back: `docker cp rmlstreamer_taskmanager_1:/mnt/data/output.nt .`
13. Print results: `cat output.nt`

## GTFS

You can re-use the same setup from above, we restart from step 7.

1. Copy data to Docker: `docker cp data/gtfs/ rmlstreamer_taskmanager_1:/mnt/data/`
2. Click on the RMLStreamer jar upload and enter the following Program Arguments: `toFile --mapping-file /mnt/data/gtfs/mapping.rml.ttl --output-path /mnt/data/output.nt`
3. Press 'Submit' and wait until the job shows 'FINISHED'
4. Copy the generated RDF back: `docker cp rmlstreamer_taskmanager_1:/mnt/data/output.nt .`
5. Print results: `cat output.nt`

# About

Tutorial for YARRRML & RMLStreamer provided by Dylan Van Assche (IDLab - Ghent University - imec).

- E-mail: dylan.vanassche@ugent.be
- Website: https://dylanvanassche.be
- Twitter: @DylanVanAssche
