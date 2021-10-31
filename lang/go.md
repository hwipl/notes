# golang

Upgrading and downgrading a dependency to a specific commit:
* https://stackoverflow.com/questions/53682247/how-to-point-go-module-dependency-in-go-mod-to-a-latest-commit-in-a-repo
* https://golang.org/doc/modules/managing-dependencies
* https://golang.org/doc/modules/gomod-ref
* https://golang.org/ref/mod
* https://golang.org/doc/modules/release-workflow

```console
$ go get <repo, module>@<commit>
$ go get github.com/someone/some_module@af044c0995fe
```
