Monolog Viewer
==============

A viewer to nicely display log files generated by [Monolog](https://github.com/Seldaek/monolog).

# Installation
1. Download Monolog Viewer and install vendors using [Composer](http://getcomposer.org/)
3. Upload the files to your webspace
4. Make sure PHP has write access to the directory `/secure` - This is where the password hash will be stored (see below). Write access can be achieved by either changing the folder's chmod to 777 (less secure) or making sure that the owner of the file is the same as the one the server is using.
5. Create a configuration file (rename or copy the `config_example.json`).
6. Open Monolog Viewer in the browser
7. Enter a password of your choice twice and click "Create login".
8. Done. You can now log in and use your installation of Monolog Viewer

# Configuration
The config file is a Json file containing the paths to your log files. Log files can be grouped. These groups are called clients, but you could also look at them as sites or whatever makes sense to you.

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

# Password management
My goal was to keep this tool so simple, that it can be installed on any shared hosting. Therefore I decicded not to use a database to store the password. 

To keep things secure, Monolog Viewer creates a randomly named file inside the folder `/secure/pwd`. This ensures that your password hash is safe, even if someone knows how this process works. 

The only way to get the password hash is via FTP and even if someone gets the file, it is still hashed using PHPs `password_hash()` function. If you use a secure password, this is pretty save.

Multiple users might be implemented in the future.

## Change password
To change your password, simply delete the `/secure/pwd` directory and open Monolog Viewer to set a new password.

# Mobile devices
The App is fully optimized for tablets and can be installed to the home screen on the iPad. It then works like a native app and features an app icon as well as a beautiful splash screen.

A smartphone optimized version is planned for the future.
