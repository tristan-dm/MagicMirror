# Deployment

## Mirror display

First, we need to make sure that the mirror display stays on and does not
enter into a screensaver. For this, if you're running Xorg, you can run
the following via an ssh session:

```shell
$ export DISPLAY=:0
$ xset -dpms
$ xset s off
```

## Set environment variables

In the `config/config.js.template`, there are a few environment variable
references. You can set an `.env` file to assign them values as such:

```env
export HVV_API_KEY='secret_value'
export HVV_API_USER='secret_value'
export GOOGLE_CALENDAR_LINK='secret_value'
```

And then set the environment variables like this:

```shell
$ source .env
```

## Run the app

Now, you can run the app with `pm2` by running the following from the project
root directory:

```shell
$ DISPLAY=:0 pm2 start npm --name "magic_mirror" -- start
```
