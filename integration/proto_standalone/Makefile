include ../env.mk

pwd:
	@pwd

clean:
	rm -f ./pb/strings/strings.pb.go
	rm -f ./pb/strings/strings.pb.goclay.go
	rm -f ./strings/strings.go
	rm -f ./strings/to_lower.go
	rm -f ./strings/to_upper.go
	rm -f main

protoc: protoc-build
	cd pb/strings && protoc --plugin=protoc-gen-goclay=$(GEN_CLAY_BIN) --plugin=protoc-gen-gofast=$(GEN_GOFAST_BIN) -I../../proto:/usr/local/include:${GRPC_GATEWAY_PATH}/third_party/googleapis --gofast_out=plugins=grpc:. --goclay_out=impl=true,impl_path=../../strings:. ../../proto/strings.proto

build:
	go build -o main main.go
	vgo build -o main .

test: pwd clean protoc build
