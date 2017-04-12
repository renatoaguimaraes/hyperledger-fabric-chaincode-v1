# hyperledger-fabric-chaincode-v1


## Pré-req
Go instalado (https://golang.org/dl/).

## Construção e Instalação do fabric e fabric-go-sdk
```
export GOPATH="/opt/blockchain/go" (pode ser o path de sua preferência)
export PATH="$PATH:$GOPATH/bin" (adicionando go no PATH)
go get github.com/hyperledger/fabric  (pull dos fontes do fabric)
go get github.com/hyperledger/fabric-sdk-go (pull do sdk go para implementação de smart contract)
cd $GOPATH/src/github.com/hyperledger/fabric-sdk-go 
```

```
cd fabric-client
go build; go install
Se der problema do pkcs11, instale:
$ sudo apt-get install libltdl-dev
```

```
cd fabric-ca-client
go build; go install
```
As bibliotecas construídas estão disponíveis em:
```
$GOPATH/pkg/linux_amd64/github.com/hyperledger/fabric/*.a
$GOPATH/pkg/linux_amd64/github.com/hyperledger/fabric-sdk-go/fabric-client.a
$GOPATH/pkg/linux_amd64/github.com/hyperledger/fabric-sdk-go/fabric-ca-client.a
```

Para instalações no Mac, encontrado o erro abaixo:

```
    # github.com/miekg/pkcs11

    /Users/joaovenancio/workspace/marbles/src/github.com/miekg/pkcs11/pkcs11.go:29:10: fatal error: 'ltdl.h' file not found

    #include <ltdl.h>

             ^

    1 error generated

    Rodar:

    brew install libtool
```

Obs: Ao executar o Makefile na raiz do projeto fabric-sdk-go a build apresenta erro na excução dos testes unitários. Esse passo foi pulado por não fazer parte do escopo da mvp. A solução de contorno foi compilar e instalar os projetos individualmente, fabric-client e fabric-ca-client.

---

Checkout Marbles (exemplos de contratos)
```
go get github.com/IBM-blockchain/marbles
```
Build Marbles
```
cd $GOPATH/src/github.com/IBM-blockchain/marbles/chaincode/src/marbles/
go build; go install
```
Erro de compilação (os contratos estão utilizando api 0.6)
```
# github.com/IBM-blockchain/marbles/chaincode/src/marbles
./read_ledger.go:108: assignment count mismatch: 3 = 2
./read_ledger.go:128: assignment count mismatch: 3 = 2
./read_ledger.go:178: assignment count mismatch: 3 = 2
./read_ledger.go:232: assignment count mismatch: 3 = 2
```

Outros exemplos
https://github.com/hyperledger/fabric/tree/master/examples/chaincode/go

Usando ultima versão do GO (Ubuntu)
https://tecadmin.net/install-go-on-ubuntu/

