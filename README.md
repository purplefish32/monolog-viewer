Monolog Viewer
==============

A viewer to nicely display log files generated by [Monolog](https://github.com/Seldaek/monolog).

[![Screenshot](https://github.com/Syonix/monolog-viewer/raw/master/img/screenshot.png)](#installation)

# Installation
1. Download [Composer](http://getcomposer.org/)
1. Execute `php composer.phar create-project syonix/monolog-viewer install-directory/` (make sure to replace `install-directory` with the name of the directory you want to install monolg viewer into.
1. Upload the files to your webspace
1. Make sure PHP has write access to the directory `/secure` - This is where the password hash will be stored (see [below](#password-management)). Write access can be achieved by either changing the folder's chmod to 777 (less secure) or making sure that the owner of the file is the same as the one the server is using.
1. Create a configuration file (rename or copy the `config_example.json`).
1. Open Monolog Viewer in the browser
1. Enter a password of your choice twice and click "Create login".
1. Done. You can now log in and use your installation of Monolog Viewer

# Configuration
The config file is a Json file containing the paths to your log files. Log files can be grouped. These groups are called clients, but you could also see them as sites or whatever makes sense to you.

To set up log files, make sure to fill in the config file following this structure:
```json
{
    "clients": [
        {
            "name": "Your first client",
            "logs": {
                "Error-Log":"http://acme.com/logs/error.log",
                "Info-Log":"http://acme.com/logs/info.log"
            }
        },
        {
            "name": "Your second client",
            "logs": {
                "Sent Mails":"http://acme-forum.com/logs/mail.log"
            }
        }
    ]
}
```
**Note:** If your `config.json` is invalid or none of your log files are readable, Monolog Viewer will display an error message. Also, if a client contains only logs that are not readable, the client will not be listed in the navigation.

# Password management
My goal was to keep this tool so simple, that it can be installed on any shared hosting. Therefore I decicded not to use a database to store the password. 

To keep things secure, Monolog Viewer creates a randomly named file inside the folder `/secure/pwd`. This ensures that your password hash is safe, even if someone knows how this process works. 

The only way to get the password hash is via FTP and even if someone gets the file, it is still hashed using PHPs `password_hash()` function. If you use a secure password, this is pretty safe.

Multiple users might be implemented in the future.

## Change password
To change your password, simply delete the `/secure/pwd` directory and open Monolog Viewer to set a new password.

# Mobile devices
The App is fully optimized for tablets and can be installed to the home screen on the iPad. It then works like a native app and features an app icon as well as a beautiful splash screen.

A smartphone optimized version is planned for the future.
