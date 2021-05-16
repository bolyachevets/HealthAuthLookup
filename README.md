# chsa
A simple, proof-of-concept web app

## Pre-requisites
- Docker
- node
- npm
- ansible

### Instructions for building and deploying locally

# Step 1
If you have ansible installed on your machine, run this single-line CLI command
```
ansible-playbook playbooks/setup.yaml
```

Otherwise, manually create a `.env` file according to [the sample env file](./.env.sample) and run
```
mkdir pg_data &&\
    cd api && npm ci && npm run build &&\
    cd ../web && npm ci && npm run build
```

# Step 2 
Run `docker-compose up` at project root path.

# Step 3
Visit http://localhost:8888 via a web browser.

If you wish to skip web ui and directly interact with api,\
the service is at http://localhost:8888 and REST endpoint description can be found in [open api doc](api/public/doc/api/index.html)\
(need to open the html in a browser).

---

### Instructions on how to query db to find out # requests

See [DB README](db/README.md)

---

### Technical Architecture Diagram 

<img width="600" alt="architecture-diagram" src="https://user-images.githubusercontent.com/22973013/118410916-c7bdc200-b646-11eb-8e01-170889b54d78.png">

### Future Roadmap
- Enable SSL for docker containers.
- Verify cross platform and cross browser compatibility.
- Develop and implement accessibility strategy (e.g., add "alt text" to fields to enable blind users)
- Add an API Gateway (e.g. Kong), which in addition to abstracting interface from implementation can provide security/analytics/monitoring services (e.g., rate limiting, load balancing, insulation via reverse proxy, logging, caching).
- Use Cassandra DB for logging (only requires 'eventual consistency' and benefits from fast writes).
