# Melhores práticas de criptografia
Slides da palestra sobre teoria e exemplos práticos de criptografia. 


## Slides
Os slides podem ser visualizados em 
[https://viniciuscampitelli.com/slides-criptografia-melhores-praticas/](https://viniciuscampitelli.com/slides-criptografia-melhores-praticas/) ou você pode
acessá-los localmente:

1. Clonar o repositório
    ```
    git clone --recursive git@github.com:vcampitelli/slides-libsodium-php.git
    ```
2. Acessar `index.html` no seu navegador

## Códigos
Há alguns códigos de exemplo na pasta `scripts`.

### `scripts/encrypt-without-hash.php`
Script em PHP que utiliza a [libsodium](https://doc.libsodium.org) para gerar uma informação (como um _access token_ ou _cookie_) criptografada responsável por identificar um usuário e, com uma simples técnica de [bit-flipping](https://en.wikipedia.org/wiki/Bit-flipping_attack), fazer um ataque força-bruta para demonstrar a importância de **sempre** fazer o _hashing_ para garantir integridade e autenticidade do dado.

Para rodar o teste, basta executar
```sh
$ php encrypt-without-hash.php
```

### `scripts/asymmetric`
`node-rsa-encrypt.js` e `node-rsa-decrypt.js` são scripts feitos em Node.js para implementar a criptografia híbrida com RSA

Para rodar os testes, basta executar
```sh
$ cd scripts/asymmetric

# Para gerar o par de chaves
$ ssh-keygen -t rsa -b 2048 -m PEM -f ./id_rsa && \
    ssh-keygen -e -m PEM -f id_rsa > id_rsa.pub

$ node node-rsa-encrypt.js
# Digitar a mensagem que deseja criptografar
# Copiar o texto criptografado

$ node node-rsa-decrypt.js
# Colar o texto criptografado copiado anteriormente
```

### `scripts/symmetric`
`node-rsa-encrypt.js` e `node-rsa-decrypt.js` são scripts feitos em Node.js para implementar a criptografia híbrida com RSA

Para rodar os testes, basta executar
```sh
$ cd scripts/symmetric
# Para gerar a chave
# Se não possuir o pwgen, você pode acessar algum site para gerar chaves
$ pwgen -sy1 32 > symmetric.key

$ node node-rsa-encrypt.js
# Digitar a mensagem que deseja criptografar
# Copiar o texto criptografado

$ node node-rsa-decrypt.js
# Colar o texto criptografado copiado anteriormente
```

