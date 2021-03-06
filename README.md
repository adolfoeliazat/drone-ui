[![Build Status](http://beta.drone.io/api/badges/drone/drone-ui/status.svg)](http://beta.drone.io/drone/drone-ui)

# drone-ui

This project contains the source code for the drone user interface. The generated javascript and css assets are embedded into a Go source file which is imported into the main drone application, using `go get`.

This is currently being tested with `node v4.4.7`

## Developing

To compile the source and create minified css and javascript assets:

```bash
npm install
npm run build
```

## Running

To run a devserver with watching, hotreloading and proxy to drone server:

```bash
npm start -- --scheme <drone scheme> \
             --host   <drone host> \
             --token  <drone api token>
```

For example:

```
npm start -- --scheme http \
             --host   localhost:8080 \
             --token  eyJhbGciOiJIUzI1NiIsInR5cCI....
```

Note you will need to retrieve your drone api token from your account settings screen in the drone user interface. When the server is running you can open the following url in your browser:

```
http://localhost:9000
```

## Contributing

Please discuss changes and enhancements in our [gitter room](https://gitter.im/drone/drone) prior to submitting a pull request. If your pull request alters the visual appearance of the user interface please include screenshots.

## Releases

To bundle and embed the code in a Go source file install the following command line utilities:

```bash
go get github.com/jteeuwen/go-bindata/...
go get github.com/elazarl/go-bindata-assetfs/...
```

To generate the Go source file run the following command:

```bash
npm run embed
```

__Note__ that for security reasons we will not accept a pull request that updates embedded Go asset file since we are not able to easily review the embedded, minified code. This file is instead automatically generated by our build server to prevent tampering.
