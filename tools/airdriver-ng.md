AIRDRIVER-NG

NAME
       airdriver-ng  -  automatically  install/uninstall and patch drivers and
       802.11 stacks

SYNOPSIS
       airdriver-ng <command> [drivernumber]

DESCRIPTION
       airdriver-ng is a script that provides  status  information  about  the
       wireless drivers on your system plus the ability to load and unload the
       drivers. Additionally, airdriver-ng allows you to install and uninstall
       drivers  complete  with  the patches required for monitor and injection
       modes. Plus a number of other functions.

COMMAND
       supported
              Lists all supported drivers

       kernel Lists all in-kernel drivers

       installed
              Lists all installed drivers

       loaded Lists all loaded drivers

       load <drivernum>
              Loads a driver

       unload <drivernum>
              Unloads a driver

       reload <drivernum>
              Reloads a driver

       install <drivernum>
              Installs a driver

       remove <drivernum>
              Removes a driver

       remove_stack <num>
              Removes a stack

       install_stack <num>
              Installs a stack

       details <drivernum>
              Prints driver details

       detect Detects wireless cards