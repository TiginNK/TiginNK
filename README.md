# TiginNK

TiginNK is a high-performance, **optimization-focused** server software for Minecraft: Bedrock Edition. It is a fork of Cloudburst Nukkit, aiming to provide a more stable and faster experience.

Written in Java, TiginNK is fast, stable, and easy to develop for.

Links
--------------------

* __[Website](https://tigin.xyz/)__
* __[Documentation](https://docs.tigin.xyz)__
* __[GitHub](https://github.com/TiginNK/TiginNK)__

Compile TiginNK
-------------
To compile from source:

```bash
git clone https://github.com/TiginNK/TiginNK
cd TiginNK
./gradlew shadowJar
```

The compiled JAR file can be found in the `build/libs/` directory.

Running
-------------
To start the server:
`java -jar tiginnk-1.0-SNAPSHOT.jar`
*(Filename may vary depending on the version)*

Docker
-------------

Running TiginNK in [Docker](https://www.docker.com/) (17.05+ or higher).

Build image from source:

```bash
docker build -t tiginnk .
```

Run once to generate the `tiginnk-data` volume, load default settings, and choose language:

```bash
docker run -it -p 19132:19132/udp -v tiginnk-data:/data tiginnk
```

Docker Compose
-------------

Use [docker-compose](https://docs.docker.com/compose/overview/) to start the server on port `19132` with the `tiginnk-data` volume:

```bash
docker-compose up -d
```

Kubernetes & Helm
-------------

Validate the chart:

`helm lint charts/nukkit`

Dry run and print out rendered YAML:

`helm install --dry-run --debug tiginnk charts/nukkit`

Install the chart:

`helm install tiginnk charts/nukkit`

Or, with different values (e.g., ARM64 and LoadBalancer):

```bash
helm install tiginnk \
  --set image.tag="arm64" \
  --set service.type="LoadBalancer" \
    charts/nukkit
```

Or, using a custom values file:

```bash
helm install tiginnk \
  -f helm-values.local.yaml \
    charts/nukkit
```

Upgrade the chart:

`helm upgrade tiginnk charts/nukkit`

Testing after deployment:

`helm test tiginnk`

Completely remove the chart:

`helm uninstall tiginnk`
