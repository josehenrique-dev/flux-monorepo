# Repositorio para demonstração da utilização de monorepo com FluxCD

---

Olá! Nesse projeto irei apresentar uma ideia para armazenar os valores de seus manifestos do Kubernetes utilizando FluxCD e HelmCharts!

**Observação 1:** É necessario a instalação de um cluster Kubernetes na sua maquina.

---

### Instalação:

```sh
curl -s https://fluxcd.io/install.sh | sudo bash
```

### Adicionando o FluxCD ao seu cluster Kubernetes:

```sh
git clone git@github.com:josehenrique-dev/flux-monorepo.git
```

```sh
cd flux-monorepo
```

```sh
export GITHUB_TOKEN=<your-token>
```

```sh
flux bootstrap github   --components-extra=image-reflector-controller,image-automation-controller   \
--owner=josehenrique-dev  --repository=flux-monorepo   --branch=main  \
--path=clusters/my-cluster/flux-system   --read-write-key   --personal
```
### Verificando se os recursos do FluxCD foram instalados corretamente:

```sh
flux check
```

```sh
kubectl get pods -n flux-system
```

```sh
kubectl get pods -n app1
```

Pronto! Caso esses dois comandos acima retornem sem erros a instalação foi feita com sucesso!
