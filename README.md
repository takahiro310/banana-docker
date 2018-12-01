# [banana-app](https://github.com/takahiro310/banana-app)用のdocker-compose

## 必要事項

### .envを環境に合わせて作成

ex)
```
RAILS_ENV=production
MYSQL_ROOT_PASSWORD=root
MYSQL_USER=banana
MYSQL_PASSWORD=banana
```

### 初回のときに・・・

* banana-docker直下にbanana-appをgit clone
* docker-compose build
* DB USER作成
```
docker-compose exec db sh

GRANT ALL PRIVILEGES ON *.* TO 'banana'@'%';
FLUSH PRIVILEGES;
```

* DBスキーマ作成
```
docker-compose exec app sh

rake db:create RAILS_ENV=production
rake db:migrate RAILS_ENV=production

rake assets:clobber RAILS_ENV=production
rake assets:precompile RAILS_ENV=production
```
