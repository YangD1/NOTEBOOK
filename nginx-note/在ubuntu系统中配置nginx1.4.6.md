### https配置
```
# 80 端口配置 并且强制重定向到https
server {
        listen 80;
        server_name localhost;
        rewrite ^(.*)$  https://$host$1 permanent;
 }

# 443 https 配置
server {
        listen 443;
        server_name localhost;

        root html;
        index index.php index.html index.htm;

        ssl on;
        ssl_certificate cert/cisa/localhost.pem;
        ssl_certificate_key cert/cisa/localhost.key;

        ssl_session_timeout 5m;

        ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers "HIGH:!aNULL:!MD5 or HIGH:!aNULL:!MD5:!3DES";
        ssl_prefer_server_ciphers on;

        location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                fastcgi_pass unix:/run/php/php7.1-fpm.sock;
                fastcgi_index index.php;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                include fastcgi_params;
                     }

        location / {
        #       try_files $uri $uri/ =404;
                try_files $uri $uri/ /index.php$is_args$args;
        }

        location ~ /\.ht {
                deny all;
        }
}
```

### 80端口配置
```
server {
	listen 80;
	server_name localhost;
	root html;
	index index.html index.php index.htm;

	location ~ \.php$ {
		fastcgi_split_path_info ^(.+\.php)(/.+)$;
		fastcgi_pass unix:/run/php/php7.1-fpm.sock;
		fastcgi_index index.php;
		fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
		include fastcgi_params;
	}

	location / {
		try_files $uri $uri/ /index.php$is_args$args;
	}

	location ~ /\.ht {
		deny all;
	}
}
```