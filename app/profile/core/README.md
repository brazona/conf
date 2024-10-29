# Credenciais Github Registry Image

Esse diretório tem o objetivo de armazenar informações variáveis e sensiveis comun entre as aplicações.

## Github

As imagens docker estão publicadas no repositório da aplicação no github, para configurar as credenciais de acesso para o Rancher realizar o pull, siga as instruções abaixo.

Gerar credenciais em base 64.

```sh
echo -n "username:123123adsfasdf123123" | base64
```

A saída desse comando:

```txt
dXNlcm5hbWU6MTIzMTIzYWRzZmFzZGYxMjMxMjM=
```

Gerar arquivo de configuração em base 64.

```sh

echo -n  '{"auths":{"ghcr.io":{"auth":"Q2V6YXJGZWxpcGU6Z2hwX3BKT0JDYjVHSjdpSDF2Q3JDU0V0ckM0bGJiRGRLUTI2cWpUdQ=="}}}' | base64

```

A saída desse comando:

```txt
eyJhdXRocyI6eyJnaGNyLmlvIjp7ImF1dGgiOiJRMlY2WVhKR1pXeHBjR1U2WjJod1gzQktUMEpE
WWpWSFNqZHBTREYyUTNKRFUwVjBja00wYkdKaVJHUkxVVEkyY1dwVWRRPT0ifX19
```


```yaml

apiVersion: v1
kind: Secret
type: kubernetes.io/dockerconfigjson
metadata:
  name: dockerconfigjson-github-com
  namespace: development
data:
  .dockerconfigjson: eyJhdXRocyI6eyJnaGNyLmlvIjp7ImF1dGgiOiJRMlY2WVhKR1pXeHBjR1U2WjJod1gzQktUMEpEWWpWSFNqZHBTREYyUTNKRFUwVjBja00wYkdKaVJHUkxVVEkyY1dwVWRRPT0ifX19

```
