# Docker GUI

Docker GUI is a web app for viewing and managing Docker images, containers, volumes, etc in a web browser.

This project is a fork of the original Docker UI project made by @otothea and that can be found [here](https://github.com/otothea/docker-ui).

The initial project that we worked on together can be found [here](https://github.com/salaheddine-zemmouri/docker-gui)

[![Docker UI Screenshot 1](https://raw.githubusercontent.com/Assifar-Karim/docker-gui/master/screenshot1.png)](https://raw.githubusercontent.com/Assifar-Karim/docker-gui/master/screenshot1.png)

[![Docker UI Screenshot 2](https://raw.githubusercontent.com/Assifar-Karim/docker-gui/master/screenshot2.png)](https://raw.githubusercontent.com/Assifar-Karim/docker-gui/master/screenshot2.png)

[![Docker UI Screenshot 3](https://raw.githubusercontent.com/Assifar-Karim/docker-gui/master/screenshot3.png)](https://raw.githubusercontent.com/Assifar-Karim/docker-gui/master/screenshot3.png)

## Usage
The usage of Docker GUI takes three forms, if you wish to install both the client and the server in your local machine then follow the **production FULL** section. However, if you only wish to install the Docker GUI server in your machine then follow the **Production Server** section. 

If you wish to contribute to Docker GUI and develop new features to the tool then you can follow the **Development** section.

### Production FULL

Build the image

```bash
docker build -t docker-gui .
```

Run it

```bash
docker run -d -p 9898:9898 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --name docker-gui docker-gui
```

Run it with authentication (see [environment variables](#environment-variables))

```bash
docker run -d -p 9898:9898 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --name docker-ui \
  -e DOCKER_UI_HTTPS=1 \
  -e DOCKER_UI_USER=username \
  -e DOCKER_UI_PASS=password \
  -e DOCKER_UI_SECRET=supersecretsessionkey \
  docker-ui
```

### Production Server

Pull the image

```bash
docker pull ghcr.io/Assifar-Karim/docker-gui-server:latest
```

Run it
```bash
docker run -d -p 9898:9898 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --name docker-gui-server\
  ghcr.io/Assifar-Karim/docker-gui-server:latest
```

### Development

Clone this fork:

```bash
git clone https://github.com/Assifar-Karim/docker-gui
```

Change to the repository directory

```bash
cd docker-gui
```

Install the dependencies 

```bash
npm install
```

Copy the config and adjust as needed (see [config options](#config-options))

```bash
cp config.example.js config.js
```

Start the client

```bash
npm run watch
```

Start the server

```bash
npm start
```

## Config Options

- **host** `string` - the hostname the API listens on
- **port** `number` - the port the API listens on
- **[debugger]** `number` - the port the debugger listens on (required if dev)
- **[https]** `boolean` - force https
- **[httpsProto]** `boolean` - trust `x-forwarded-proto` header (only set to `true` if you know you need this)
- **[user]** `string` - the username to access the UI
- **[pass]** `string` - the password to access the UI (required if `user` is set)
- **[secret]** `string` - the express session key (required if `user` is set)

## Environment Variables

- **DOCKER_UI_HOST** - override config.host
- **DOCKER_UI_PORT** - override config.port
- **DOCKER_UI_DEBUGGER** - override config.debugger
- **DOCKER_UI_HTTPS** - override config.https
- **DOCKER_UI_HTTPS_PROTO** - override config.httpsProto
- **DOCKER_UI_USER** - override config.user
- **DOCKER_UI_PASS** - override config.pass
- **DOCKER_UI_SECRET** - override config.secret

## Testing

- ✅ Unit Tests.
- 🔲 Integration Tests.

## Contributing

Pull requests are welcome.

## Contributors

- [Assifar Karim](https://github.com/Assifar-Karim) 
- [Charkaoui Khalil](https://github.com/khalil99-68)
- [Dahman Iliass](https://github.com/iliass-dahman)
- [Imeghri Sami](https://github.com/imeghri-sami)
- [Zemmouri Salah Eddine](https://github.com/salaheddine-zemmouri)
