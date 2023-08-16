# TODO List

## Server Requirements Lavarel 7.x
- [x] PHP >= 7.2.5
- [x] BCMath PHP Extension
- [x] Ctype PHP Extension
- [x] Fileinfo PHP extension
- [x] JSON PHP Extension
- [x] Mbstring PHP Extension
- [x] OpenSSL PHP Extension
- [x] PDO PHP Extension
- [x] Tokenizer PHP Extension
- [x] XML PHP Extension

## Laradock

1. Entre do diretório ```/home/user``` e crie uma pasta para os seus projetos. Neste exemplo, vou chamar de ```meus-projetos```.
```
mkdir meus-projetos
```
> [!NOTE]
> Neste tutorial, estou utilizando WSL2 com a imagem Ubuntu-22.04.2 LTS. 

2. Entre na pasta ```meus-projetos```, clone o repositório do Laravel e renomeie a pasta conforme seu interesse. Neste exemplo, vou chamar de ```laravel-com-docker```.
```
cd meus-projetos
```
```
git clone git@github.com:laravel/laravel.git laravel-com-docker
```

> [!NOTE]
> Caso precise de uma versão específica do Laravel, por exemplo a versão 7.0.0, é necessário informar a ```branche/tag``` no comando ```git clone```. 
```
git clone -b v7.0.0 --single-branch git@github.com:laravel/laravel.git laravel-com-docker
```

3. Entre na pasta ```laravel-com-docker```, clone o repositório Laradock.
```
cd laravel-com-docker
```
```
git clone git@github.com:laradock/laradock.git
```

4. Entre na pasta ```laradock```, e renomeie ```.env.example``` para ```.env```.
```
cd laradock
```
```
cp .env.example .env
```

> [!NOTE]
> Edite o arquivo ```.env``` para defininir as configiurações personalizadas. Lembre-se, por padrão vem o ```PHP_VERSION=7.4``` e caso precise alterar, basta substituir por um dos valores disponíveis.

5. Execute seus contêineres e aguarde a conlusão do processo.
```
docker-compose up -d nginx mysql phpmyadmin redis workspace
```

6. Liste os containers, copie a CONTAINER_ID e entre no container ```laradock-workspace```. Em seguida, execute o comando ```composer install``` e aguarde a conlusão do processo.
```
docker ps
```
```
docker exec -it CONTAINER_ID bash
```
```
composer install
```

7. Saia do container ```laradock-workspace``` e retorne a pasta ```laravel-com-docker```. Em seguida, renomeie ```.env.example``` para ```.env```.
```
exit
```
```
cd ..
```
```
cp .env.example .env
```

8. Entre novamente no container ```laradock-workspace``` e gere a ```key:generate```.
```
docker ps
```
```
docker exec -it CONTAINER_ID bash
```
```
php artisan key:generate
```

## Observações
- [ ] php 7.4.6 (instalado 7.4.33)
- [x] php 7.4-mbstring
- [x] php 7.4-dom
- [ ] composer 1.10.7 (instalado 2.5.8)
- [ ] redis 6.2.4 (instalado 7.0.12)
- [ ] composer create-project --prefer-dist laravel/laravel projeto_laravel_via_composer "7.0"