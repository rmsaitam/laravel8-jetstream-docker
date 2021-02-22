# laravel8-jetstream-docker
**Laravel 8 + Jetstream no ambiente Docker**

Premissas: Ter o Git, Docker e Docker compose instalado

Após fazer o fork deste repositório, clona o repositório forkado na sua conta do GitHub

`git clone https://github.com/SUACONTAGITHUB/laravel8-jetstream-docker.git`

`cd laravel8-jetstream-docker` 

`docker-compose up -d` 

Após fazer o build e subir o ambiente

`docker-compose exec php-apache composer install` 

`cp src/app/.env.example src/app/.env` 

Edite o arquivo .env e adicione as credencias do banco de dados 
```
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laraveljetstream
DB_USERNAME=root
DB_PASSWORD=secret
```
Adicionar no arquivo hosts 

127.0.0.1 app.intranet 

No browser, acesse http://app.intranet:8001 para criar o banco de dados e depois executar as migrations, conforme segue:

`docker-compose exec php-apache php artisan jetstream:install livewire`

`docker-compose exec php-apache php artisan jetstream:install livewire --teams`

`docker-compose exec php-apache php artisan migrate`

`docker-compose exec php-apache php artisan key:generate`

Instalação do NPM e Node.js via NVM (controle de versão do Node.js)

`docker exec -it php8-apache bash` 
 
 Dentro do container php8-apache, execute na ordem, conforme segue abaixo:
 
  `curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.35.3/install.sh | bash`

 `source ~/.bashrc && nvm install v14.15.5`

  `npm install && npm run dev`

  `chown -R www-data:www-data storage`

No browser, acesse http://app.intranet:8000 crie um novo usuário no link "register", após criar o usuário irá autenticar e redirecionar no dashboard automaticamente.

Feito!
