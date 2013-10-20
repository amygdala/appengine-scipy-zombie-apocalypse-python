## appengine-scipy-zombie-apocalypse

This is a fork of the Google Cloud Platform [VM Runtime Zombie Apocalypse](https://github.com/GoogleCloudPlatform/appengine-scipy-zombie-apocalypse-python) sample. It is modified to show how you can deploy multiple Modules as part of the same app, with one of the modules the Zombie Apocalypse VM Runtime module, and the other a very simple 'guestbook' app that uses 'regular' App Engine instances.

The module routing is set up so that the guestbook is reached at `http://your-app-id.appspot.com`, and the zombies dashboard is reached at `http://your-app-id.appspot.com/zombies`.

The original sample is inspired by a [Zombie Apocalypse ODEINT demo][1] listed in the [Scipy Cookbook][2].


## Deploying

1. Make sure that you are invited to the [VM Runtime Trusted Tester
   Program][3], and download the custom SDK.

2. In both `app.yaml` and `zombies.yaml`, change the `application` value of the `app.yaml` file from
   `your-app-id` to that of the Application ID which is whitelisted for the VM  Runtime Trusted Tester Program.

3. Change to your project directory.  From there, run the following commands:

        <CUSTOM_SDK_DIR>/appcfg.py --no_precompilation -R update app.yaml zombies.yaml
        <CUSTOM_SDK_DIR>/appcfg.py --no_precompilation -R update_indexes .
        <CUSTOM_SDK_DIR>/appcfg.py --no_precompilation -R update_dispatch .

4. Visit the following URLs:
   `http://your-app-id.appspot.com/`
   and
   `http://your-app-id.appspot.com/zombies`


## How to check the logs on the VMs

The module logs are available at the App Engine Admin Console, [https://preview.appengine.google.com/](https://preview.appengine.google.com/).  (For the VM runtime, be sure to always use the 'preview' prefix).

Sometimes you may want to to check the logs on the VMs as well. To do that:

0. Install [gcutil][4] if necessary.
1. Go to the [Cloud Console][5] and choose the project which is under
   the Trusted Tester Program.
2. Click 'Compute Engine' in the sidebar.
3. Find your VM runtime instance: Click the instance for the version `one`, or the version you are using
   if you changed it from `one`.
4. In the instance details, scroll down to the bottom and find the
   clickable word "ssh", and click it.
5. Copy the displayed command and execute it on your command line.
6. Look at `/var/log/app_engine/*.log`.


## Contributing changes

* See [CONTRIB.md](CONTRIB.md)


## Licensing

* See [LICENSE](LICENSE)


[1]: http://wiki.scipy.org/Cookbook/Zombie_Apocalypse_ODEINT
[2]: http://wiki.scipy.org/Cookbook/
[3]: https://docs.google.com/document/d/1VH1oVarfKILAF_TfvETtPPE3TFzIuWqsa22PtkRkgJ4
[4]: https://developers.google.com/compute/docs/gcutil/
[5]: https://cloud.google.com/console
