# System build

build:
	go build -buildmode=c-shared -ldflags="-w -s" -o handler.so
	chown `stat -c "%u:%g" .` handler.so

pack:
	zip handler.zip handler.so
	chown `stat -c "%u:%g" .` handler.zip

# Docker build

dbuild:
	@docker run --rm \
		-v $(GOPATH):/go \
		-v $(PWD):/usr/src/current \
		-w /usr/src/current \
		eawsy/aws-lambda-go make build

dpack:
	@docker run --rm \
		-v $(GOPATH):/go \
		-v $(PWD):/usr/src/current \
		-w /usr/src/current \
		eawsy/aws-lambda-go make pack

clean:
	@rm -rf handler.zip handler.so
