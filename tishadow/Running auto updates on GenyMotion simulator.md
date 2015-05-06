In a terminal, navigate to the `tishadowapp` directory, and run

```
tishadow server
```

In a separate terminal, navigate to the directory of the app you want to run.  Run

```
tishadow run
```

Go to the emulator and open the tishadow app.  Enter the IP address that was showed when you started the server.  You should see the app you started, then, in the list.  Select it to open.

Once the app is installed and running on the device, you can push only the updated files by running

```
tishadow run --update
  or
tishadow run --patch
```

More info on that [here](http://tishadow.yydigital.com/deploy)

NOTES:

- To install the tishadow app on a GenyMotion emulator, you will need to install Google Play Apps on it.  This is fairly cumbersome, and instructions can be found [here](http://stackoverflow.com/questions/20635134/genymotion-emulator-installation-error-install-failed-missing-shared-library).
- You can run the tishadow app on a physical device, and connect to your tishadow server on your local machine, if they are on the same wifi network.  On the app, use the 10.0... address of the tishadow server.
