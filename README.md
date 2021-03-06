﻿# Laravel7-登入系統範例


## 開發者注意事項
:warning: 若專案建立後程式碼Pull到local端下來無法執行, 此狀況為正常現象
* 要在local端測試部屬提供兩種方式，透過安裝docker來進行專案快速專案部屬或直接修改我您作業系統的環境變數(或是採用.env)
* 若非用docker快速部屬想直接採用原本安裝在作業系統上的資料庫的話，請設定環境變數
```env
`db_host`: 指向到您的資料庫，例如localhost或是其他IP
`db_name`: 指向到您的資料庫名稱
`db_username`: 指向到您的資料庫使用者名稱
`db_password`: 指向到您的資料庫密碼
```

## 修改程式碼注意事項
1. 修改資料庫連線  
由於系統採用固定獨特的環境變數作為資料庫連線方法, 因此專案的資料庫連線部分請勿更動`app/config/database.php`內的
```php
        'mysql' => [
            'driver' => 'mysql',
            'url' => env('DATABASE_URL'),
            'host' => env('db_host', '127.0.0.1'),
            'port' => env('DB_PORT', '3306'),
            'database' => env('db_name', 'forge'),
            'username' => env('db_username', 'forge'),
            'password' => env('db_password', ''),
            'unix_socket' => env('DB_SOCKET', ''),
            'charset' => 'utf8mb4',
            'collation' => 'utf8mb4_unicode_ci',
            'prefix' => '',
            'prefix_indexes' => true,
            'strict' => true,
            'engine' => null,
            'options' => extension_loaded('pdo_mysql') ? array_filter([
                PDO::MYSQL_ATTR_SSL_CA => env('MYSQL_ATTR_SSL_CA'),
            ]) : [],
        ],
```
2. 修改框架版本  
而框架版本若非laravel:7, 想要更換框架版本請至`Dockefile`修改為自己想要的版本(如需要本機上做測試則須一併連同`Dockerfile.local`去做修改)
3. Laravel .env  
若有進階需求需使用到`.env`檔案的話，可以修改於`app/.env.example`檔案內，部屬時會作為`.env`檔案做處理
4. 部屬環境額外環境變數
若開發需求上可能有針對專案需要的特別環境變數，由於目前此需求不再系統開發考慮範圍內，因此可能要麻煩使用者透過修改`Dockerfile`的形式去加入
```dockerfile
ENV 環境變數名稱1 值1
ENV 環境變數名稱2 值2
ENV 環境變數名稱3 值3
```
## 程式碼參考教學來源
[Laravel Login Registration Tutorial](https://www.soengsouy.com/2020/04/laravel-7-register-and-login-account.html?m=1)


## reference
[Laravel Login Registration Tutorial](https://www.soengsouy.com/2020/04/laravel-7-register-and-login-account.html?m=1)
