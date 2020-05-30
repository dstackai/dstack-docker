[dstack.ai](https://dstack.ai) is a collaborative application that enables data scientists 👩🏽‍🔬and their distributed teams to work effectively together on data exploration and deliver results faster . 

The features of dstack.ai includes:

* Building interactive dashboards
* Management of datasets
* Scheduling jobs to process data and publish visualizations

The platform offers data-scientists friendly APIs to share data, and an online platform for non-tech people to collaborate with data scientists.

The Docker image can be used to host dstack.ai on own servers or in own AWS/Azure/Google Cloud account. 

You can run dstack.ai in Docker using the following command:

```bash
docker run -d --name <dstack container name> \
-v <path to data directory>:/data \
-p <port on host>:8080 -e dstackai_port=<public port> \
-e dstackai_smtp_host=<SMTP server host> \
-e dstackai_smtp_port=<SMTP server port> \
-e dstackai_smtp_user=<SMTP server user> \
-e dstackai_smtp_password=<SMTP server password> \
-e dstackai_smtp_starttls=true \
-e dstackai_smtp_from=<admin email address> \
dstackai/dstackai:latest
```

If you'd like to test how the Docker image works without configuring an SMTP server, you can try to run it via the `docker-compose.yml` from this repository:

```bash
docker-compose up
```   

Note, the `docker-compose.yml` is using [bytemark/smtp](https://hub.docker.com/r/bytemark/smtp/) to send emails. Since it's not a production SMTP server, emails might get into the Spam folder. For the production setup, it's recommended to use s real SMTP server. 