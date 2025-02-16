```
http {
   # Настроить upstream для балансировки нагрузки
   upstream backend_servers {
       server backend1.example.com;
       server backend2.example.com;
       server backend3.example.com;
   }

   # Создать ключ для лимита на основе IP клиента
   limit_req_zone $binary_remote_addr zone=rate_limit_zone:10m rate=10r/m;

   server {
       listen 80;

       location / {
           # Применить лимит запросов
           limit_req zone=rate_limit_zone burst=5;

           # Указать код ошибки для возврата если лимит достигнут
           limit_req_status 429;

           # Проксировать запрос на upstream
           proxy_pass http://backend_servers;
       }
   }
}
```
