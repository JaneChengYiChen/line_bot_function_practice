# README #

### Install###

1. Clone project
2. Install composer

    ```
    curl -sS https://getcomposer.org/installer | php
    ```

3. Install package (under project directory)

    ```
    php composer.phar install
    ```
4. create link

```
~/www/bot_practice -> ~/Leishan/bot_practice/www/
```

### Nginx ###
```
#bot_practice
server {
    listen       9008;
    server_name  localhost;

    #charset koi8-r;

    access_log  /Users/ming/log/nginx/bot-practice.access.log;
    error_log /Users/ming/log/nginx/bot-practice.error.log;

    location / {
        root  /Users/ming/www/leishan_service/;
        try_files $uri $uri/ /index.php?$args /api.php?$args;
        index  index.php;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   html;
    }
    location ~ \.php$ {
        root  /Users/ming/www/;
        fastcgi_pass   127.0.0.1:9010;
        fastcgi_index  index.php;
        fastcgi_param SCRIPT_FILENAME /Users/user/www/$fastcgi_script_name;
        include        fastcgi_params;
    }
}
```

### Requirement ###

- PHP 7.2 and above version (Line bot )
- php7.2-curl
- php7.2-mbstring (unicode)
- php7.2-mysql
- php7.2-sybase (mssql)

### Prepare PHP environment ###
- Use homebrew to install PHP

	```
	brew tap homebrew/dupes
	```

	```
	brew tap homebrew/versions
	```

	```
	brew tap homebrew/homebrew-php
	```

	```
	brew install php56 --with-cgi, --with-fpm, --with-homebrew-curl, --with-mssql
	```


### Testing ###

- use postman & [newman](https://github.com/postmanlabs/newman)

### Config ###

```
config:
  line:
    channel_id: {id}
    channel_secret: {secret}
    channel_access_token: {token}
  luis:
    api_host: https://westus.api.cognitive.microsoft.com/luis/api/v2.0/apps/
    host: https://southeastasia.api.cognitive.microsoft.com/luis/v2.0/apps/
    km_tia:
      app_id: {appid}
      subscription_key: {key}
      api_subscription_key: {key}
      closedlist_id: {closedlistid}
```# line_bot_function_practice
