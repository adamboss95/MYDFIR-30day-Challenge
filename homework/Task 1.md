

## Web Server Setup & Automation

**Objective**: Set up a Nginx web server with automated deployment of a static website.  

Tasks:


- Install Nginx and ensure it starts on boot.
```
sudo apt install nginx
```

```
sudo systemctl enable nginx
```

- Create a directory /var/www/lab-site and add a sample index.html with the text "Welcome to Intern Lab"
```
cd /var/www/
```

```
mkdir lab-site
```

```
touch index.html
```

edit the file index.html using vim
```
vim index.html
```

add these lines in the editor
```
welcome to intern lab
```



-  Configure Nginx to Serve the Site on Port 8080

Now, configure Nginx to serve the site from `/var/www/lab-site` on port 8080. Create a new configuration file for your site.

```
sudo nano /etc/nginx/sites-available/lab-site

```

Add the following configuration to the file:
```
server {
    listen 8080;
    server_name localhost;

    root /var/www/lab-site;
    index index.html;
}
```

creating a soft link 
sudo ln -s /etc/nginx/sites-available/lab-site /etc/nginx/sites-enabled/


- Write a script (deploy.sh) to automate copying files from /home/user/web-files to /var/www/lab-site and reload Nginx


```
#!/bin/bash


sourceDir="/home/user/web-files"
destinationDir="/var/www/lab-site"


sudo cp -r "$sourceDir"/* "$destinationDir"


sudo systemctl reload nginx


echo "Successfully Files copied from $sourceDir to $destinationDir and Nginx is reloaded"
```

assigning permission
```
chmod a+x deploy.sh
```


- Use cron to run the script every day at 2 AM.

```
crontab -e
```

add these lines inside crontab
```
0 2 * * * /home/abdulwahab/deploy.sh
```