# Recovering Your WordPress Admin Credentials

Did you just make a new WordPress app on NorthStack and already forgot your admin credentials? We get it. In this article, we'll show you how to get your WordPress admin credentials.

### Username and Email

1. To view your admin username or email, begin by locating your NorthStack app's main directory on your local machine.
2. Next, locate the directory for the environment that you want to get the credentials for and jump into it.
3. Once inside that environment's subdirectory, you should see a **build.json** file. Go ahead and open it up with your favorite text editor. It should look something like this:
   ```json
   {
       "wordpress-install": {
           "url": "ns-xxxxxxxxxxxxxxxx.dev-us-east-1-northstack.com",
           "title": "WordPress Example",
           "admin_user": "example_username",
           "admin_email": "user@example.com",
           "multisite": false,
           "subdomains": false
       }
   }
   ```
4. See the fields labeled **admin_user** and **admin_email**? That's your username and email address for your WordPress admin user!

### Password

To find the password that was used to set up the admin user on the first deploy of your new app, you'll want to fetch the app's secrets.
Your WordPress password will not continue to be synced to the app's secrets system if you change your password later.

Run the secrets list command with the `--show` flag to see the password that was set when the app was initially deployed:
```shell
northstack secrets:list <app name> <environment> --show
```

Updating this secret after the first deploy of the app will not affect the WordPress password in any way, it is only saved for reference purposes.
