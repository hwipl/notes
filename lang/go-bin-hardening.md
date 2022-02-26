# go build binaries with static, pie, relro

* https://www.redhat.com/en/blog/hardening-elf-binaries-using-relocation-read-only-relro
* https://pkg.go.dev/cmd/link
* https://pkg.go.dev/cmd/go#hdr-Compile_packages_and_dependencies
* https://go-review.googlesource.com/c/go/+/312509/
* https://github.com/golang/go/pull/45681

Building with pie and relro:

```console
$ go build -buildmode=pie -ldflags "-linkmode external -extldflags '-z relro -z now'" ./cmd/something
```

Use static linking:

extldflags: add "-static" or "--static-pie" --> linker warning:

```
warning: Using 'getaddrinfo' in statically linked applications requires at
runtime the shared libraries from the glibc version used for linking
```

* https://stackoverflow.com/questions/2725255/create-statically-linked-binary-that-uses-getaddrinfo
  * "glibc uses libnss to support a number of different providers for address
    resolution services. Unfortunately, you cannot statically link libnss, as
    exactly what providers it loads depends on the local system's
    configuration."
  * "Meanwhile in version 2.20 there is the --enable-static-nss flag of
    configure which seems to do exactly this. Note that static linking
    introduces some disadvantages (see @pixelbeat's answer and the comments
    made to it)."

* https://stackoverflow.com/questions/37630274/what-do-these-go-build-flags-mean-netgo-extldflags-lm-lstdc-static
  * answer 1
* https://go.dev/src/net/net.go

--> tag netgo? usergo?
