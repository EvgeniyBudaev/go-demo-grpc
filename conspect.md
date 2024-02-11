Инициализация зависимостей
```
go mod init github.com/EvgeniyBudaev/go-demo-grpc
```

Сборка
```
go build -v ./cmd/
```

Удаление неиспользуемых зависимостей
```
go mod tidy -v
```

Вызовите утилиту protoc для генерации соответствующих go-файлов.
Для этого выполните команду:
```
protoc --go_out=. --go_opt=paths=source_relative \
  --go-grpc_out=. --go-grpc_opt=paths=source_relative \
  proto/demo.proto
```
В --go-out запишется файл с кодом для Protobuf-сериализации.
В --go-grpc_out сохранится файл с gRPC-интерфейсами и методами.
Так как вы указали параметр paths=source_relative, сгенерированные файлы создадутся в поддиректории ./proto.
Если бы указали параметр paths=import, то сгенерированные файлы создались бы в директории,
указанной в директиве go_package, то есть ./demo/proto.

gRPC
Protocol Buffer Compiler Installation
https://grpc.io/docs/protoc-installation/
```
sudo apt install -y protobuf-compiler
protoc --version
```
После этого установите утилиты, которые отвечают за кодогенерацию go-файлов:
```
go get -u google.golang.org/grpc
go get -u google.golang.org/protobuf
```
