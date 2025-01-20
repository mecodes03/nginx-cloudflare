The config file should be placed in /etc/nginx/sites-available/ directory. A common naming convention would be to name it after your domain, so you could call it:

    /etc/nginx/sites-available/mecodes.duckdns.org



After creating the file, you'll need to enable it by creating a symbolic link in the sites-enabled directory:

    sudo ln -s /etc/nginx/sites-available/mecodes.duckdns.org /etc/nginx/sites-enabled/



install Certbot for free SSL:

    sudo apt install certbot python3-certbot-nginx



Get SSL certificate:

    sudo certbot --nginx -d mecodes.duckdns.org



now set up the nginx config for the site


Test Nginx Configuration:

    sudo nginx -t



Reload Nginx:

    sudo systemctl reload nginx



Verify the Setup:

    curl -I https://mecodes.duckdns.org



Check Logs for Errors:

General debug logs:

    sudo tail -f /var/log/nginx/debug.log



Proxy-specific errors:

    sudo tail -f /var/log/nginx/proxy_error.log



Use the New Key to Connect:

    ssh -i ~/Downloads/new-key.pem ubuntu@<INSTANCE_PUBLIC_IP>

