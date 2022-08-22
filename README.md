# test-operator-openshift-4

Ejemplo de *operator controller* para la plataforma openshift 4

## Aclaraciones

Se tuvo que modificar el archivo **Makefile** en la parte de `helm-operator` porque en algunas distros no funcionaba el comando `install`, esto porque no se podia bajar
una version existente de helm por armar mal la URL a causa de que los comandos que ejecuta para armarla devuelven cosas diferentes.

Para solucionar el problema se hardcodeo una version que sí existe con estas lineas:

```sh
curl -LO https://github.com/operator-framework/operator-sdk/releases/download/v1.3.0/helm-operator_linux_amd64 ;\
mv helm-operator_linux_amd64 ./bin/helm-operator ;\
```

## Despliegue

### Requisitos

* Estar conectado en un cluster de openshift o kubernetes
* podman instalato en la pc

### Comandos

```bash
make bundle
make bundle-build
make bundle-push
make podman-build
make podman-push
make project-create
make bundle-deploy-on-cluster
```

## Documentacion

* [Pasos a seguir por Redhat](https://docs.openshift.com/container-platform/4.7/operators/operator_sdk/helm/osdk-helm-tutorial.html#osdk-helm-tutorial)
* [Operador SDK](https://docs.openshift.com/container-platform/4.3/operators/operator_sdk/osdk-getting-started.html)
