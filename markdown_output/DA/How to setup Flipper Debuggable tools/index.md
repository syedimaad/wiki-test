1.  Download [Facebook Flipper](https://fbflipper.com/)

2.  Install the above-downloaded application based on your OS

3.  Launch the Application, and go to troubleshoot \> setup doctor.

4.  Resolve common and Android Sections to make sure prerequisites are
    completed.

    1.  Install requires dependency via `brew` / other command line
        tools available based on your OS\
        For brew:

        bashbrew update brew upgrade brew install watchman

    2.  If `brew` is not installed, use the following commands

        1.  /bin/bash -c \"\$(curl -fsSL
            https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)\"

            Then it will give 2 more commands to run to add it to the
            profile like

        2.  (echo; echo \'eval \"\$(/opt/homebrew/bin/brew
            shellenv)\"\') \>\> /Users/kajal.kumari/.zprofile eval
            \"\$(/opt/homebrew/bin/brew shellenv)\"

*Please note: the above commands will be printed in the terminal. You
can copy and paste the same to complete the installation.*

5.  Use the existing Android SDK install path.

Get the SDK Location using Android SDK manager

When setup is completed

6.  Once set up is complete. Run the application version which includes
    flipper changes.

7.  When enable you will see device connected like below.

8.  We can enable / disable available plugins. Please note: All plugins
    are not available and might required set up programmatically.\

    Flipper Sidebar after plugins are enabled, setup is completed and
    device with flipper SDK running.

## Advantage of using Flipper

- No need to inspect app process again and again during application
  restart.

- Plugin like Network, Database, Shared Preference might be better
  compare to Stetho.

## Important Links

[https://fbflipper.com/](https://fbflipper.com/){card-appearance="inline"}

[https://fbflipper.com/docs/features/](https://fbflipper.com/docs/features/){card-appearance="inline"}

[https://fbflipper.com/docs/features/plugins/network/](https://fbflipper.com/docs/features/plugins/network/){card-appearance="inline"}\
\
[https://github.com/facebook/flipper](https://github.com/facebook/flipper){card-appearance="inline"}
