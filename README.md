# unzip

```shell
go get github.com/blacklat/unzip
```

```go
package main

import (
    "fmt"
    "github.com/blacklat/unzip"
)

func main() {
    unZip := unzip.New("test.zip","/tmp/test")
    files, err := unZip.Extract()
    if err != nil {
        fmt.Println(err)
    } else {
        fmt.Println(files)
    }
}
```

...

```go
if tmpDir, err := ioutil.TempDir("/tmp", "dirPrefix-"); err != nil {
  fmt.Println(err)
  return
} else {
  defer os.RemoveAll(tmpDir)
  unZip := unzip.New("test.zip",tmpDir)
  if files, err := unZip.Extract(); err != nil {
    fmt.Println(err)
    return
  } else {
    for f := range files {
      fmt.Println(files[f])
    }
  }
}
```
