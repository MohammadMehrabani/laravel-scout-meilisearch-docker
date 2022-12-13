- Run `docker load -i laravel9-nginx.tar.gz`
- Run `docker load -i laravel9-php.tar.gz`
- Run `docker load -i laravel9-artisan.tar.gz`
- Run `docker load -i laravel9-composer.tar.gz`


- Run `mkdir meilisearch`
- Run `sudo rm -f src/README.md`
- Run `docker-compose up -d`
- Run `docker-compose run --rm composer create-project laravel/laravel .`
- Run `docker-compose run --rm composer require laravel/scout`
- Run `docker-compose run --rm artisan vendor:publish --provider="Laravel\Scout\ScoutServiceProvider"`
- Run `docker-compose run --rm composer require meilisearch/meilisearch-php http-interop/http-factory-guzzle`

### random key generate for `MEILI_MASTER_KEY` value in `meilisearch.env` file
```
openssl rand -hex 30
# output: 173e95f077590ed33dad89247247be8d8ce8b6722ccc87829aaefe3207be

# meilisearch.env
MEILI_MASTER_KEY="173e95f077590ed33dad89247247be8d8ce8b6722ccc87829aaefe3207be"
```
### set in `.env` file
```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret

SCOUT_DRIVER=meilisearch
MEILISEARCH_HOST=http://meilisearch:7700
MEILISEARCH_KEY=173e95f077590ed33dad89247247be8d8ce8b6722ccc87829aaefe3207be
```