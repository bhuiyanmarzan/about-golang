# 1. System Design
# 2. Database Design
# 3. How setup project

### initialize projext
```bash
go mod init github.com/codersgyan/olx-api
```

### create a project entry point
```bash
# main.go
package main

import "fmt"

func main() {
	fmt.Println("Olx-api server is running...")
}
```

### Run this application /first build then run
```bash
go run main.go # build + execute in single command
```

### Production
in production application first build this project then run the application, never run `go run` in production

Build command
```bash
go build -o bin/main main.go # -o Output folder /bin/main
```

Run command
```bash
./bin/main
```

### Makefile (Task Runner Tool)
work with make file
```bash
# Makefile
build:
	go build -o bin/main main.go
run:
	./bin/main
```

Run makefile in bash
```bash
make build  # To build this project
make run    # Run this build file
```
now showing result this type
```text
./bin/main
Olx-api server is running..
```
if you don't want to see this folder name update the Makefile
```bash
# Makefile
build:
	@go build -o bin/main main.go
run:
	@./bin/main
```

if folder name and command name same this showing this error `make: 'build' is up to date. ` to solve this problem 
```makefile
# Makefile
.PHONY: build run
build:
	@go build -o bin/main main.go
run: build # dependency build + run
	@./bin/main
```

fix folder structure every main file create a single binary
```bash
    api     # api separate binary --> bin
    ws      # ws separate binary --> bin
    worker  # worker separate binary --> bin
    cli     # cli separate binary --> bin
/olx-api
    /cmd
        /api
            main.go # This main file create new api binary
```
update makefile
```makefile
.PHONY: build run
build:
	@go build -o bin/api/main ./cmd/api
run: build
	@./bin/api/main
```
initilize git
```bash
git init
```

add .gitignore file
```bash
.gitignore
```
