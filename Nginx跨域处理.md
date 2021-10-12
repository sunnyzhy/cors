# Nginx 跨域处理

***注: 如果前端部署在 nginx 服务里，那么前端相当于不跨域，和正常请求一样，无需额外配置。***

```conf
location /api {
        add_header Access-Control-Allow-Origin *;
        add_header Access-Control-Allow-Methods 'GET, POST, OPTIONS';
        add_header Access-Control-Allow-Headers 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';
        if ($request_method = 'OPTIONS') {
            return 200;
        }

        proxy_pass http://localhost:8090;
}
```
