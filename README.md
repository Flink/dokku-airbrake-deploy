# dokku-airbrake-deploy

dokku-airbrake-deploy is a plugin for [dokku][dokku] that notifies [Airbrake][airbrake] (or [Errbit][errbit]) that your application has been deployed.

## Requirements

`curl` is required and will be installed when calling `dokku plugins-install-dependencies`.

## Installation

```sh
$ sudo git clone https://github.com/Flink/dokku-airbrake-deploy.git /var/lib/dokku/plugins/airbrake-deploy
$ dokku plugins-install-dependencies
```

## Commands

```
$ dokku help
    airbrake-deploy <app>                           Display the current airbrake deploy hook status of app
```

## Usage

Checking if deploy hook is enabled or not on your application:
```
# dokku airbrake-deploy my-app            # Server side
$ ssh dokku@server airbrake-deploy my-app # Client side

AIRBRAKE_API_KEY is not defined for my-app
$
```

To enable deploy hook for you application, you just have to set AIRBRAKE\_API\_KEY:
```
# dokku config:set my-app AIRBRAKE_API_KEY=your_api_key            # Server side
$ ssh dokku@server config:set my-app AIRBRAKE_API_KEY=your_api_key # Client side
```

By default the repository URL provided will be the one from dokku (dokku@your.host:my-app). To change that, just set AIRBRAKE\_REPO\_URL to your real repository (eg. git@github.com/user/repo.git).

This plugin is also compatible with [Errbit][errbit], set AIRBRAKE\_BASE\_URL to your errbit installation to notify it (eg. https://my.errbit.net).

## License

This plugin is released under the MIT license. See the file [LICENSE](LICENSE).

[dokku]: https://github.com/progrium/dokku
[airbrake]: https://airbrake.io
[errbit]: http://errbit.github.io/errbit/
